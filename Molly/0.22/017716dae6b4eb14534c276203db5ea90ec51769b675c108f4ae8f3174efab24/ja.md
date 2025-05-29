```
TriclinicBoundary(v1, v2, v3; approx_images=true)
TriclinicBoundary(SVector(v1, v2, v3); approx_images=true)
TriclinicBoundary(SVector(l1, l2, l3), SVector(α, β, γ); approx_images=true)
TriclinicBoundary(arr; approx_images=true)
```

3つの `SVector{3}` 基底ベクトルまたは基底ベクトルの長さと角度 α/β/γ（ラジアン）によって定義されるトリクリニック3Dバウンディングボックス。

最初の基底ベクトルはx軸に沿って指向し、2番目はxy平面内に存在しなければなりません。最小画像規則を使用する際に最も近い周期的画像を見つけるために近似が使用されます。この近似は、最短のボックスの高さ/幅の半分より短い距離に対して正確です。キーワード引数 `approx_images` を `false` に設定すると、正確な最も近い画像が見つかりますが、これは遅くなります。

現在、立方体ボックスをシミュレートすることはできません。代わりに [`CubicBoundary`](@ref) または小さなオフセットを使用してください。無限境界とは現在互換性がありません。
