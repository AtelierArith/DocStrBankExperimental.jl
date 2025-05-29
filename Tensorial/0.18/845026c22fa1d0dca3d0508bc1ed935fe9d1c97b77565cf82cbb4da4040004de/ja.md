```
fromvoigt(S::Type{<: Union{SecondOrderTensor, FourthOrderTensor}}, A::AbstractArray{T}; [order])
fromvoigt(S::Type{<: Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor}}, A::AbstractArray{T}; [order, offdiagscale])
```

配列 `A` を Voigt 形式から型 `S` のテンソルに変換します。

キーワード引数:

  * `offdiagscale`: 非対角要素のスケーリング係数を決定します。
  * `order`: Voigt 順序を決定する直交インデックスのベクトル (`Tuple{Int, Int}`)。デフォルトの順序は `[(1,1), (2,2), (3,3), (2,3), (1,3), (1,2), (3,2), (3,1), (2,1)]` で、`dim=3` の場合です。

!!! note
    `offdiagscale` は **Voigt 形式** における非対角要素のスケーリング係数であるため、`fromvoigt` では `1/offdiagscale` で乗算されます。したがって、`fromvoigt(tovoigt(x, offdiagscale = 2), offdiagscale = 2)` は元の `x` を返します。


他に [`tovoigt`](@ref) も参照してください。

# 例

```jldoctest
julia> fromvoigt(Mat{3,3}, 1.0:1.0:9.0)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 1.0  6.0  5.0
 9.0  2.0  4.0
 8.0  7.0  3.0

julia> fromvoigt(SymmetricSecondOrderTensor{3},
                 1.0:1.0:6.0,
                 offdiagscale = 2.0,
                 order = [(1,1), (2,2), (3,3), (1,2), (1,3), (2,3)])
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 1.0  2.0  2.5
 2.0  2.0  3.0
 2.5  3.0  3.0
```
