```
backproject_filtered(sinogram, θs; 
                        geometry, μ, filter)
```

フィルタ付き逆投影アルゴリズムを使用して、`sinogram` から画像を再構成します。

  * `filter=nothing`: フーリエ空間で適用されるフィルタ。`nothing` の場合、ランプフィルタが使用されます。`filter` は、シノグラムと同じ長さの1D配列である必要があります。

キーワード引数の説明については、[`radon`](@ref)を参照してください。
