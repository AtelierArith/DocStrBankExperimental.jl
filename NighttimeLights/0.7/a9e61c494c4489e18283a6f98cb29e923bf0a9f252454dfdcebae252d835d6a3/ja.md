`centre_of_mass` は、夜間の光の放射データキューブによって重み付けされた座標の平均を求めます。

```julia
spaster = sparse(Array(radiance_image)[:,:,1])
centre_of_mass(spaster, dims(radiance_image))
```
