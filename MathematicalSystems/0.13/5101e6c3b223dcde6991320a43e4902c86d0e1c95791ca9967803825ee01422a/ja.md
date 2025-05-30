```
IdentityMultiple{T} < AbstractMatrix{T} where T
```

与えられた次数と数値型の単位行列のスカラー倍。

### フィールド

  * `M` – 型 `T` の一様スケーリング演算子
  * `n` – 単位行列のサイズ

### 注意事項

この型は、指定されたサイズの単位行列の倍数を作成するために使用できます。倍数と次数のみが保存されるため、メモリの割り当ては最小限です。

内部的に、この型はJuliaの遅延単位演算子 `UniformScaling` をラップしています。`IdentityMultiple` は `AbstractMatrix` をサブタイプ化しているため、通常の行列演算や `AbstractMatrix` に対するディスパッチで使用できます。

`UniformScaling` と `IdentityMultiple` の違いは、前者のサイズが一般的であるのに対し、後者のサイズは固定されていることです。

### 例

行列のサイズのみを指定すると、単位行列を表します：

```jldoctest identitymultiple
julia> using MathematicalSystems: IdentityMultiple

julia> I2 = Id(2)
IdentityMultiple{Float64} of value 1.0 and order 2

julia> I2 + I2
IdentityMultiple{Float64} of value 2.0 and order 2

julia> 4*I2
IdentityMultiple{Float64} of value 4.0 and order 2
```

スケーリング（デフォルトは `1.0`）は、第二引数として渡すことができます：

```jldoctest identitymultiple
julia> I2r = Id(2, 1//1)
IdentityMultiple{Rational{Int64}} of value 1//1 and order 2

julia> I2r + I2r
IdentityMultiple{Rational{Int64}} of value 2//1 and order 2

julia> 4*I2r
IdentityMultiple{Rational{Int64}} of value 4//1 and order 2
```

または、`UniformScaling`（`I`）を渡してコンストラクタを使用します：

```jldoctest identitymultiple
julia> using LinearAlgebra

julia> I2 = IdentityMultiple(2.0*I, 2)
IdentityMultiple{Float64} of value 2.0 and order 2

julia> I2r = IdentityMultiple(2//1*I, 2)
IdentityMultiple{Rational{Int64}} of value 2//1 and order 2
```
