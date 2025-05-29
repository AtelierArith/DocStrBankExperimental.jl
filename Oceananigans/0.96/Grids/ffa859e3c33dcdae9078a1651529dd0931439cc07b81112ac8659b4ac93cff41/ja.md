```
nodes(grid, (ℓx, ℓy, ℓz); reshape=false, with_halos=false)
nodes(grid, ℓx, ℓy, ℓz; reshape=false, with_halos=false)
```

`grid`のネイティブ座標の内部ノードに対するビューの3タプルを、`loc=(ℓx, ℓy, ℓz)`の位置で`x, y, z`に返します。

`reshape=true`の場合、ビューは`x, y, z`それぞれに対して非単一次元1, 2, 3の3D配列に再形成されます。これらの再形成された配列は、3Dフィールドや配列とのブロードキャスト操作に使用できます。

`RectilinearGrid`の場合、ネイティブ座標は`x, y, z`です。曲線格子の場合、例えば`LatitudeLongitudeGrid`や`OrthogonalSphericalShellGrid`では、ネイティブ座標は`λ, φ, z`です。

[`xnodes`](@ref)、[`ynodes`](@ref)、[`znodes`](@ref)、[`λnodes`](@ref)、および[`φnodes`](@ref)を参照してください。
