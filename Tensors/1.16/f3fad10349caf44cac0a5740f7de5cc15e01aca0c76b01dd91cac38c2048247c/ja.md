```
fromvoigt(S::Type{<:AbstractTensor}, A::AbstractArray{T}; kwargs...)
```

配列 `A` を Voigt 形式から型 `S` のテンソルに変換します。

キーワード引数:

  * `offset`: 配列 `A` のどこからテンソルが始まるかのオフセットインデックス。4次のテンソルの場合、キーワード引数はそれぞれ `offset_i` と `offset_j` です。デフォルトは `0` です。
  * `offdiagscale`: オフダイアゴナル要素のスケーリングファクターを決定します。この引数は `SymmetricTensor` のみ適用されます。`frommandel` は "Mandel" 形式にも使用でき、`SymmetricTensor` のために `offdiagscale = √2` を設定し、`Tensor` のための `fromvoigt` と同等です。
  * `order`: Voigt 順序を決定する線形インデックスの行列。デフォルトのインデックス順序は `[11, 22, 33, 23, 13, 12, 32, 31, 21]` で、`order = [1 6 5; 9 2 4; 8 7 3]` に対応します。

他にも [`tovoigt`](@ref) を参照してください。

```jldoctest
julia> fromvoigt(Tensor{2,3}, 1.0:1.0:9.0)
3×3 Tensor{2, 3, Float64, 9}:
 1.0  6.0  5.0
 9.0  2.0  4.0
 8.0  7.0  3.0
```
