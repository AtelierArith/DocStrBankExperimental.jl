```
apply!([α=1,] [P=Direct,] A::Mapping, x, [scratch=false,] [β=0,] y) -> y
```

は `y` を `α*P(A)⋅x + β*y` で上書きします。ここで `P ∈ Operations` は `Direct`、`Adjoint`、`Inverse` および/または `InverseAdjoint` のいずれかで、適用するマッピング `A` のバリアントを示します。慣例として、`β = 0` の場合は `y` の以前の内容は全く使用されないため、`y` は初期化されていなくても結果を格納するために直接使用できます。`scratch` のオプション引数は、呼び出し元によって入力 `x` がもはや必要ないかどうかを示し、そのためスクラッチ配列として使用できることを示します。`scratch = true` または `β = 0` は、特定のマッピングタイプの `apply!` メソッドの実装によって、一時的な作業領域の割り当てを回避するために利用される可能性があります。

`apply!` メソッドは `LinearAlgebra.mul!` メソッドの一般化と見なすことができます。

引数の順序は変更可能で、次のようにしても同じ結果が得られます：

```
apply!([β=0,] y, [α=1,] [P=Direct,] A::Mapping, x, scratch=false) -> y
```

結果 `y` は次のようにして割り当てられた可能性があります：

```
y = vcreate(P, A, x, scratch=false)
```

または次のようにして：

```
y = vcreate(A, x, scratch=false)
```

`P` が指定されていない場合です。

マッピングのサブタイプは、特定のシグネチャで `vcreate` と `apply!` を拡張するだけで済みます：

```
vcreate(::Type{P}, A::M, x, scratch::Bool=false) -> y
apply!(α::Number, ::Type{P}, A::M, x, scratch::Bool, β::Number, y) -> y
```

サポートされている任意の操作 `P` に対して、`M` はマッピングの型です。もちろん、引数 `x` と `y` の型も指定できます。

オプションとして、次のシグネチャを持つメソッド：

```
apply(::Type{P}, A::M, x, scratch::Bool=false) -> y
```

も拡張して、デフォルトの実装を改善することができます：

```
apply(P::Type{<:Operations}, A::Mapping, x, scratch::Bool=false) =
    apply!(1, P, A, x, scratch, 0, vcreate(P, A, x, scratch))
```

参照： [`Mapping`](@ref), [`apply`](@ref), [`vcreate`](@ref).
