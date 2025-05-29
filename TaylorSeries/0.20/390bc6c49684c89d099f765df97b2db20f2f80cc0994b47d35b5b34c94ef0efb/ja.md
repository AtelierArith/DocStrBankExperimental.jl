```
set_variables([T::Type], names::String; [order=get_order(), numvars=-1])
```

独立変数を表す各エントリを持つ `TaylorN{T}` ベクトルを返します。`names` は各変数の出力を定義します（スペースで区切られています）。デフォルトの型 `T` は `Float64` で、`order` のデフォルトはグローバルに定義されたものです。`order` または `numvars` を変更すると、hash_tables がリセットされます。

`numvars` が指定されていない場合、`names` から推測されます。変数名が1つだけ定義されていて `numvars>1` の場合、この名前を異なる変数のための添字付きで使用します。

```julia
julia> set_variables(Int, "x y z", order=4)
3-element Array{TaylorSeries.TaylorN{Int},1}:
  1 x + 𝒪(‖x‖⁵)
  1 y + 𝒪(‖x‖⁵)
  1 z + 𝒪(‖x‖⁵)

julia> set_variables("α", numvars=2)
2-element Array{TaylorSeries.TaylorN{Float64},1}:
  1.0 α₁ + 𝒪(‖x‖⁵)
  1.0 α₂ + 𝒪(‖x‖⁵)

julia> set_variables("x", order=6, numvars=2)
2-element Array{TaylorSeries.TaylorN{Float64},1}:
  1.0 x₁ + 𝒪(‖x‖⁷)
  1.0 x₂ + 𝒪(‖x‖⁷)
```
