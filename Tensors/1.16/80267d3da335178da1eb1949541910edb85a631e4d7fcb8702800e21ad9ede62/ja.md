```
tovoigt!(v::AbstractArray, A::Union{SecondOrderTensor, FourthOrderTensor}; kwargs...)
```

テンソルを「Voigt」形式に変換します。インデックスの順序は次の通りです: `[11, 22, 33, 23, 13, 12, 32, 31, 21]`。

キーワード引数:

  * `offset`: テンソルを配列 `A` のどこに格納するかのオフセットインデックス。4次のテンソルの場合、キーワード引数はそれぞれ `offset_i` と `offset_j` です。デフォルトは `0` です。
  * `offdiagscale`: 非対角要素のスケーリング係数を決定します。この引数は `SymmetricTensor` のみ適用されます。`frommandel!` は「Mandel」形式にも使用でき、`SymmetricTensor` のために `offdiagscale = √2` を設定し、`Tensor` のための `fromvoigt!` と同等です。
  * `order`: Voigt 順序を決定する線形インデックスの行列。デフォルトのインデックス順序は `[11, 22, 33, 23, 13, 12, 32, 31, 21]` です。

さらに [`tovoigt`](@ref) と [`fromvoigt`](@ref) を参照してください。

```jldoctest
julia> T = rand(Tensor{2,2})
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.218587
 0.549051  0.894245

julia> x = zeros(4);

julia> tovoigt!(x, T)
4-element Vector{Float64}:
 0.32597672886359486
 0.8942454282009883
 0.21858665481883066
 0.5490511363155669

julia> x = zeros(5);

julia> tovoigt!(x, T; offset=1)
5-element Vector{Float64}:
 0.0
 0.32597672886359486
 0.8942454282009883
 0.21858665481883066
 0.5490511363155669
```
