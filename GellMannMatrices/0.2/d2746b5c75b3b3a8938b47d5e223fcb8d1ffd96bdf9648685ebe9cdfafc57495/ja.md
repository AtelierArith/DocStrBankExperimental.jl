```
gellmann([T::Type{<:AbstractMatrix} = Matrix{ComplexF64},] d::Integer;
         skip_identity = true, normalize = false)
```

`d` 次元の一般化されたゲルマン行列を、型 `T` の行列のベクトルとして返します。

`T` は、`eltype(T)` が任意の複素浮動小数点型である任意の可変 `AbstractMatrix`（`SparseMatrixCSC` を含む）であることができます。

## キーワード引数

  * `skip_identity`（デフォルト、`true`）：`false` の場合、次元 `d` の単位行列が返されるベクトルの最後の要素として含まれます。
  * `normalize`（デフォルト、`false`）：`true` の場合、行列は直交正規性の関係 `tr(Mᵢ'*Mⱼ) = 2δᵢⱼ` を確保する方法で正規化されます；`false` の場合、単純さを優先した行列要素の選択が行われます（すなわち、整数要素）。

## 例

パウリ行列 $σ_i$ (`d=2`) とゲルマン行列 $Λ_i$ (`d=3`) を計算します：

```jl
julia> σᵢ = gellmann(2)
julia> Λᵢ = gellmann(3)
```
