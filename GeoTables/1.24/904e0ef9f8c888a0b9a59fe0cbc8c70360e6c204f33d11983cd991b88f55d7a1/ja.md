```
georef(tuple)
```

名前付き `tuple` を `CartesianGrid(dims)` にジオリファレンスし、`dims` はタプルに格納された配列から取得されます。

## 例

```julia
julia> georef((a=rand(10, 10), b=rand(10, 10))) # 2D グリッド
julia> georef((a=rand(10, 10, 10), b=rand(10, 10, 10))) # 3D グリッド
```
