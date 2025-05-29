```
tovoigt([type::Type{<:AbstractArray}, ]A::Union{SecondOrderTensor, FourthOrderTensor}; kwargs...)
```

テンソルを「Voigt」形式に変換します。

オプション引数:

  * `type`: 返される配列の型を決定します。可能な型は `Array` と `SArray` です（[`StaticArrays`](https://juliaarrays.github.io/StaticArrays.jl/stable/)を参照）。

キーワード引数:

  * `offdiagscale`: 非対角要素のスケーリング係数を決定します。この引数は `SymmetricTensor` のみに適用されます。`tomandel` は「Mandel」形式にも使用でき、`SymmetricTensor` に対して `offdiagscale = √2` を設定し、`Tensor` に対しては `tovoigt` と同等です。
  * `order`: Voigt 順序を決定する線形インデックスの行列です。デフォルトのインデックス順序は `[11, 22, 33, 23, 13, 12, 32, 31, 21]` で、`order = [1 6 5; 9 2 4; 8 7 3]` に対応します。

[`tovoigt!`](@ref) および [`fromvoigt`](@ref) も参照してください。

```jldoctest
julia> tovoigt(Tensor{2,3}(1:9))
9-element Vector{Int64}:
 1
 5
 9
 8
 7
 4
 6
 3
 2

julia> tovoigt(SymmetricTensor{2,3}(1:6); offdiagscale = 2)
6-element Vector{Int64}:
  1
  4
  6
 10
  6
  4

julia> tovoigt(Tensor{4,2}(1:16))
4×4 Matrix{Int64}:
 1  13   9  5
 4  16  12  8
 3  15  11  7
 2  14  10  6

julia> using StaticArrays: SMatrix

julia> tovoigt(SMatrix, Tensor{4,2}(1:16))
4×4 SMatrix{4, 4, Int64, 16} with indices SOneTo(4)×SOneTo(4):
 1  13   9  5
 4  16  12  8
 3  15  11  7
 2  14  10  6
```
