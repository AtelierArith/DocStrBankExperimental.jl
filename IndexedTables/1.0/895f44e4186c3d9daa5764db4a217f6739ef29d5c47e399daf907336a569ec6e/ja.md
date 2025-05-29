```
table(cols; kw...)
```

抽象ベクトルの（名前付き）タプルからテーブルを作成します。

```
table(cols::AbstractVector...; names::Vector{Symbol}, kw...)
```

提供された `cols` からテーブルを作成し、オプションで `names` を指定します。

```
table(cols::Columns; kw...)
```

タプルのベクトルからテーブルを構築します。 [`rows`](@ref) と [`Columns`](@ref) を参照してください。

```
table(t::Union{IndexedTable, NDSparse}; kw...)
```

テーブルまたは NDSparse をコピーして新しいテーブルを作成します。入力と同じ主キーが使用されます。

```
table(x; kw...)
```

`Tables.jl` インターフェースに従う任意のオブジェクト `x` から `IndexedTable` を作成します。

# キーワード引数オプション:

  * `pkey`: ソートする列を選択し、主キーとします。
  * `presorted = false`: データは主キー列で事前にソートされていますか？
  * `copy = true`: `true` の場合、入力ベクトルのコピーを作成します。 `chunks` が指定されている場合は無関係です。
  * `chunks::Integer`: テーブルを分配します。 オプションは次のとおりです：

      * `Int` – （チャンクの数）安全な選択肢は `using Distributed` の後の `nworkers()` です。
      * `Vector{Int}` – 各 `length(chunks)` チャンクの要素数。

# 例:

```
table(rand(10), rand(10), names = [:x, :y], pkey = :x)

table(rand(Bool, 20), rand(20), rand(20), pkey = [1,2])

table((x = 1:10, y = randn(10)))

table([(1,2), (3,4)])
```
