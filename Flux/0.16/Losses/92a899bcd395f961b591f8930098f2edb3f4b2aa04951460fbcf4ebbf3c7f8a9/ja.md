```
binary_focal_loss(ŷ, y; agg=mean, gamma=2, eps=eps(eltype(ŷ)))
```

バイナリ*フォーカル*ロスを返します。入力の'ŷ'は正規化されていることが期待されます（すなわち、[softmax](@ref Softmax)の出力）。

`gamma = 0`の場合、損失は数学的に[`Losses.binarycrossentropy`](@ref)と同等です。

マルチクラス設定については、[`Losses.focal_loss`](@ref)も参照してください。

# 例

```jldoctest
julia> y = [0  1  0
            1  0  1]
2×3 Matrix{Int64}:
 0  1  0
 1  0  1

julia> ŷ = [0.268941  0.5  0.268941
            0.731059  0.5  0.731059]
2×3 Matrix{Float64}:
 0.268941  0.5  0.268941
 0.731059  0.5  0.731059

julia> Flux.binary_focal_loss(ŷ, y) ≈ 0.0728675615927385
true
```
