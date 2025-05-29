```
StructuredExpression{T,F,N,E,TS,D} <: AbstractStructuredExpression{T,F,N,E,D} <: AbstractExpression{T,N}
```

この式の型は、複数の式を事前定義された方法で組み合わせることを可能にします。

# パラメータ

  * `T`: 式の数値値の型。
  * `F`: 各式を単一の式に結合する構造関数の型。
  * `N`: 式内のノードの型。
  * `E`: 式の型。
  * `TS`: それらの内部式を含む名前付きタプルの型。
  * `D`: メタデータの型、別の名前付きタプル。

# 使用法

例えば、`f` と `g` の2つの式を作成し、それらを新しい式 `f_plus_g` に組み合わせることができます。これは、単にそれらを加算するコンストラクタ関数を使用します：

```julia
kws = (;
    binary_operators=[+, -, *, /],
    unary_operators=[-, cos, exp],
    variable_names=["x", "y"],
)
f = parse_expression(:(x * x - cos(2.5f0 * y + -0.5f0)); kws...)
g = parse_expression(:(exp(-(y * y))); kws...)

f_plus_g = StructuredExpression((; f, g); structure=nt -> nt.f + nt.g)
```

今、`f_plus_g` を評価すると、この式の型は `f` と `g` の結果を加算した結果を返します。

特定の構造化式に対して、上記で定義された関数 `F` を持つ2番目の型パラメータでディスパッチすることができます：

```julia
my_factory(nt) = nt.f + nt.g

Base.show(io::IO, e::StructuredExpression{T,typeof(my_factory)}) where {T} = ...
```

これにより、その関数に対して定義されたこの式の型に特有の新しいメソッドが作成されます。
