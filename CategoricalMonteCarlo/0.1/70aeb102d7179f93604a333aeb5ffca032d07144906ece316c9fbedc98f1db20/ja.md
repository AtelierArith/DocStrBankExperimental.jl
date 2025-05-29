```
normalize1!(A::AbstractArray{<:Real})
```

`A`の値を正規化して、`sum(A) ≈ 1` かつ `0 ≤ A[i] ≤ 1` ∀i となるようにします。これはL¹ノルムとは少し異なり、`abs(A[i])`を使用する必要があります。`0 ≤ A[i] < Inf` ∀iであると仮定します。`Inf`の値は処理されず、`NaN`が生成されます。

参照: [`normalize1`](@ref)

```jldoctest
julia> normalize1!([1.0, 2.0, 3.0])
3-element Vector{Float64}:
 0.16666666666666666
 0.3333333333333333
 0.5

julia> normalize1!([1.0, 2.0, Inf])
3-element Vector{Float64}:
   0.0
   0.0
 NaN

julia> normalize1!([1.0, 2.0, NaN])     # NaNは予想通り伝播します
3-element Vector{Float64}:
 NaN
 NaN
 NaN

julia> normalize1!([1.0, -2.0, 3.0])    # L¹ノルムではありません
3-element Vector{Float64}:
  0.5
 -1.0
  1.5
```
