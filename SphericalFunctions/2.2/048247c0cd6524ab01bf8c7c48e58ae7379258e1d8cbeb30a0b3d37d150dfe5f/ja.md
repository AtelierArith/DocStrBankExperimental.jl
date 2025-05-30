```
sorted_ring_pixels(s, ℓₘₐₓ, [T=Float64])
```

球面 𝕊² を $(ℓₘₐₓ+1)²-s²$ ピクセルで覆い、[`sorted_rings`](@ref) によって提供されるリングに分布させます。この関数のドキュメントで詳細を確認してください。

返される量は、各ピクセルの球面座標を含む 2-SVectors のベクターです。対応する `Rotor` については、[`sorted_ring_rotors`](@ref) も参照してください。
