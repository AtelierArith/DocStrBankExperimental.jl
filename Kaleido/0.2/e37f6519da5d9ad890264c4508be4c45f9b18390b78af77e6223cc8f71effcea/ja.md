# Kaleido: 便利なレンズ

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://tkf.github.io/Kaleido.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://tkf.github.io/Kaleido.jl/dev) [![GitHub Actions](https://github.com/tkf/Kaleido.jl/workflows/Run%20tests/badge.svg)](https://github.com/tkf/Kaleido.jl/actions?query=workflow%3ARun+tests) [![Codecov](https://codecov.io/gh/tkf/Kaleido.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/tkf/Kaleido.jl) [![Coveralls](https://coveralls.io/repos/github/tkf/Kaleido.jl/badge.svg?branch=master)](https://coveralls.io/github/tkf/Kaleido.jl?branch=master) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![GitHub commits since tagged version](https://img.shields.io/github/commits-since/tkf/Kaleido.jl/v0.2.7.svg?style=social&logo=github)](https://github.com/tkf/Kaleido.jl)

Kaleido.jlは、[Setfield.jl](https://github.com/jw3126/Setfield.jl)の上に構築された便利な[`Lens`](https://jw3126.github.io/Setfield.jl/latest/index.html#Setfield.Lens)とヘルパー関数/マクロのコレクションです。

## 機能

### 概要

  * バッチ/多値更新。`@batchlens`、`MultiLens`を参照してください。
  * 複数のネストされたフィールドを`StaticArray`または任意の多値コンテナとして取得/設定します。`getting`を参照してください。
  * 異なるパラメータ化でフィールドを取得/設定します。`converting`、`setting`、`getting`を参照してください。
  * `set`および`get`中に他のフィールドを計算します。つまり、フィールド間に制約を追加します。`constraining`を参照してください。
  * 動的に計算された位置を取得/設定します。`FLens`を参照してください。

### バッチ/多値更新

マクロ`@batchlens`は、複雑な不変オブジェクト内のさまざまなネストされた位置を更新するために使用できます：

```jldoctest README
julia> using Setfield, Kaleido

julia> lens_batch = @batchlens begin
           _.a.b.c
           _.a.b.d[1]
           _.a.b.d[3] ∘ settingas𝕀
           _.a.e
       end;

julia> obj = (a = (b = (c = 1, d = (2, 3, 0.5)), e = 5),);

julia> get(obj, lens_batch)
(1, 2, 0.0, 5)

julia> set(obj, lens_batch, (10, 20, Inf, 50))
(a = (b = (c = 10, d = (20, 3, 1.0)), e = 50),)
```

(`settingas𝕀`が何をするかは下記を参照してください。)

### 複数のネストされたフィールドを`StaticArray`として取得/設定

フィールドの値をベクトルとして取得することはしばしば便利です（例：Optim.jlで合成オブジェクトを最適化する場合）。これは、`getting(f)`を使用して行うことができ、ここで`f`はコンストラクタです。

```jldoctest README
julia> using StaticArrays

julia> lens_vec = lens_batch ∘ getting(SVector);

julia> @assert get(obj, lens_vec) === SVector(1, 2, 0.0, 5)

julia> set(obj, lens_vec, SVector(10, 20, Inf, 50))
(a = (b = (c = 10.0, d = (20.0, 3, 1.0)), e = 50.0),)
```

### 異なるパラメータ化でフィールドを取得/設定

Kaleido.jlには、フィールドを正、負、または`[0, 1]`の範囲に制限するためのレンズ`settingasℝ₊`、`settingasℝ₋`、および`settingas𝕀`が付属しています。同様に、これらのドメインで値を取得するためのレンズ`gettingasℝ₊`、`gettingasℝ₋`、および`gettingas𝕀`もあります。命名は[TransformVariables.jl](https://github.com/tpapp/TransformVariables.jl)から借用されています。

```jldoctest README
julia> lens = (@lens _.x) ∘ settingasℝ₊;

julia> get((x=1.0,), lens)  # log(1.0)
0.0

julia> set((x=1.0,), lens, -Inf)
(x = 0.0,)
```

Kaleido.jlは、[TransformVariables.jl](https://github.com/tpapp/TransformVariables.jl)で定義された`AbstractTransform`とも動作します：

```jldoctest README
julia> using TransformVariables

julia> lens = (@lens _.y[2]) ∘ setting(as𝕀);

julia> obj = (x=0, y=(1, 0.5, 3));

julia> get(obj, lens)
0.0

julia> @assert set(obj, lens, Inf).y[2] ≈ 1
```

`converting`を使用してアドホックな変換アクセサを定義することも非常に簡単です：

```jldoctest README
julia> lens = (@lens _.y[2]) ∘
           converting(fromfield=x -> parse(Int, x), tofield=string);

julia> obj = (x=0, y=(1, "5", 3));

julia> get(obj, lens)
5

julia> set(obj, lens, 1)
(x = 0, y = (1, "1", 3))
```

### `set`および`get`中に他のフィールドを計算する

`constraining`を使用してフィールド間に制約を追加することは簡単です。たとえば、フィールド`.c`が`.a`と`.b`の合計でなければならないという制約を課すことができます：

```jldoctest README
julia> obj = (a = 1, b = 2, c = 3);

julia> constraint = constraining() do obj
           @set obj.c = obj.a + obj.b
       end;

julia> lens = constraint ∘ MultiLens((
           (@lens _.a),
           (@lens _.b),
       ));

julia> get(obj, lens)
(1, 2)

julia> set(obj, lens, (100, 20))
(a = 100, b = 20, c = 120)
```

最後の行で`.c`も更新されることに注意してください。

### 動的に計算された位置を取得/設定

`FLens`を使用して、リンクリストの最後のエントリなどを`get`および`set`できます。
