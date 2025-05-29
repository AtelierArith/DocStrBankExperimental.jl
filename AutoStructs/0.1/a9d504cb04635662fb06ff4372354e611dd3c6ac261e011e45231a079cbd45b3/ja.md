```
@structdef function MyType(args...; kws...); ...; return MyType(f1, f2, ...); end
```

これは新しい型を簡単に定義するためのマクロです。

通常、新しい `struct` を定義する手順は次のとおりです。

1. 必要なフィールドを持つ `struct MyType` を定義します。
2. フィールドを初期化する `MyType(arg1, arg2, ...)` のようなコンストラクタ関数を定義します。

このマクロは、手順2のコンストラクタ定義を取り込み、戻り行を使用してフィールド名を自動的に推測し、`struct` を定義することで、これらの手順を1つにまとめます。

さらに、フィールドの名前や型を変更すると、`struct` 定義が自動的に置き換えられます。これは、この定義が自動生成された名前を使用しているためであり、`MyType` はそれへのエイリアスになります。このおかげで、Revise.jl ワークフローの大きな制限を克服しながら、異なるフィールド名や型で簡単に実験できます。

サブタイピングもサポートされており、戻り行に `<: Supertype` を追加することで実現できます。

## 例

```julia
@structdef function Layer(din::Int, dout::Int)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer(weight, bias)
end

layer = Layer(2, 4)
layer isa Layer  # true
```

上記の `@structdef` 定義は、次のコードと同等です。

```julia
@kwdef struct Layer001{T1, T2}
    weight::T1
    bias::T2
end

function Layer001(din::Int, dout::Int)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer001(weight, bias)
end

Layer = Layer001

Base.show(io::IO, x::Layer) = ... # きれいに表示するための処理
Base.show(io::IO, ::MIME"text/plain", x::Layer) = ... 
```

`Layer001{T1, T2}` は任意のオブジェクトを保持できるため、`Layer("hello", "world")` のようなものも含まれます。したがって、`struct` 自身のコンストラクタとあなたのコンストラクタ関数の間に曖昧さが生じることはありません。2つが同じ数の引数を持つ場合、入力引数の型制限（上記の例のように）や戻り行で曖昧さを回避できます。

```julia
@structdef function Layer(din, dout)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer(weight::AbstractMatrix, bias::AbstractVector)
end

layer = Layer(2, 4)
```

これにより、次のような struct が作成されます。

```julia
@kwdef struct Layer002{T1<:AbstractMatrix, T2<:AbstractVector}
    weight::T1
    bias::T2
end
```

そして、`Layer = Layer002` に再割り当てされます。

最後に、別の型のサブタイプである struct を定義することもできます。

```julia
abstract type AbstractLayer end

@structdef function Layer(din, dout)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer(weight, bias) <: AbstractLayer
end

layer = Layer(din=2, dout=4)
@assert layer isa AbstractLayer
```

対応する struct 定義は次のようになります。

```julia
@kwdef struct Layer003{T1, T2} <: AbstractLayer
    weight::T1
    bias::T2
end
```
