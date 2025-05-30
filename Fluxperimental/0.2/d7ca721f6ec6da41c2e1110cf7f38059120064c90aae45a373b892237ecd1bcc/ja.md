```
@autostruct function MyLayer(d); ...; MyLayer(f1, f2, ...); end
```

これは新しいレイヤーを簡単に定義するためのマクロです。

Fluxレイヤーは、パラメータ配列を含む可能性のある呼び出し可能な`struct`であることを思い出してください。通常、新しいレイヤーを定義する手順は次のとおりです。

1. 必要なフィールドを持つ`struct MyLayer`を定義し、Fluxに`@layer MyLayer`（または以前のバージョンでは`@functor`）を使って内部を見させます。
2. パラメータを初期化するコンストラクタ関数`MyLayer(d::Int)`を定義します（例えば、`randn32(d, d)`に初期化し、`struct`のインスタンスを返します。例えば、`m::MyLayer`）。
3. 構造体を呼び出し可能にすることで、フォワードパスを定義します: `(m::MyLayer)(x) = ...`

ステップ2の関数を考慮すると、このマクロはステップ1を処理します。ステップ3は自分で行います。

フィールドの名前や型を変更すると、`struct`定義は自動的に置き換えられ、Juliaを再起動する必要はありません。これは、この定義が自動生成された名前`== MyLayer`を使用しているためです。（ただし、古い`struct`の既存のインスタンスは何の変更も受けません！）

`@autostruct :expand function MyLayer(d)`と書くと、`@layer :expand MyLayer`が使用され、コンテナスタイルのきれいな印刷が得られます。

非Flux用途を目的としたこのマクロのバージョンについては、[AutoStructs.jl](https://github.com/CarloLucibello/AutoStructs.jl)を参照してください。

## 例

```julia
@autostruct function MyModel(d::Int)
  alpha, beta = [Dense(d=>d, tanh) for _ in 1:2]    # ここに任意のコード、キーワードのようなものだけではない
  beta.bias[:] .= 1/d
  return MyModel(alpha, beta)  # これは非常にシンプルでなければならず、=記号は許可されません（returnはオプション）
end

function (m::MyModel)(x)  # フォワードパスは通常のstructのように見えます
  y = m.alpha(x)
  z = m.beta(y)
  (x .+ y .+ z)./3
end

Flux.trainable(m::MyModel) = (; m.alpha)  # 必要に応じて、どのフィールドが学習可能かを制限します

Base.show(io::IO, m::MyModel) =  # 必要に応じて、デフォルトの印刷"MyModel(...)"を置き換えます
  print(io, "MyModel(", size(m.alpha.weight, 1), ")")

MyModel(2) isa MyModel  # true
```

ここでマクロによって定義された`struct`は次のようなものです。

```julia
struct MyModel001{T1, T2}
  alpha::T1
  beta::T2
end
```

これは任意のオブジェクトを保持できます。例えば、`MyModel("hello", "world")`のように。`methods(MyModel)`を見ればわかるように、`struct`自身のコンストラクタと`MyModel(d::Int)`の間に曖昧さが生じることはありません。

また、構造体で許可される型を制限することもできます：

```
@autostruct :expand function MyOtherModel(d1, d2, act=identity)
  gamma = Embedding(128 => d1)
  delta = Dense(d1 => d2, act)
  MyOtherModel(gamma::Embedding, delta::Dense)  # structはこれらの型のみを保持します
end

(m::MyOtherModel)(x) = softmax(m.delta(m.gamma(x)))  # フォワードパス

methods(MyOtherModel)  # 3つのメソッドが表示されます
```

そのような制限は、構造体を次のように変更します：

```julia
struct MyOtherModel002{T1 <: Embedding, T2 <: Dense}
  gamma::T1
  delta::T2
end
```

追加のコンストラクタメソッドを追加する必要がある場合、明白な構文は機能しません。しかし、次のように型に追加することができます：

```julia
MyModel(str::String) = MyModel(parse(Int, str))
# ERROR: cannot define function MyModel; it already has a value

(::Type{MyModel})(str::String) = MyModel(parse(Int, str))
MyModel("4")  # これは機能します
```

## `@compact`との比較

比較のために、`@compact`を使用してほぼ同じことを行うと、次のようになります - 短いですが、通常のJuliaコードからは遠くなります。

```julia
function MyModel2(d::Int)
    alpha, beta = [Dense(d=>d, tanh) for _ in 1:2]
    beta.bias[:] .= 1/d
    @compact(; alpha, beta) do x
        y = alpha(x)
        z = beta(y)
        (x .+ y .+ z)./3
    end
end

MyModel2(2) isa Fluxperimental.CompactLayer  # 簡単なstruct型はありません

MyOtherModel2(d1, d2, act=identity) =
  @compact(gamma = Embedding(128 => d1), delta=Dense(d1 => d2, act)) do x
    softmax(delta(gamma(x)))
  end
```
