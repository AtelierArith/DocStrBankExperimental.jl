```
current2arrows(f, x, y; excluded = nothing)
```

2D物理空間における前方電流ベクトルを計算します。

`(u, v)`を返します。ここで、`u[i]`と`v[i]`は、`(x, y)`を中心とし、各他の点の`f[i,:]`による加重平均の方向を指すベクトルの`x`および`y`成分です。

### 引数

  * `f`: [`stationary_statistics`](@ref)から計算された`forward_current`。
  * `x`: 点の`Vector` `[x1, x2, ...]`
  * `y`: 点の`Vector` `[y1, y2, ...]`

### オプション引数

  * `excluded`: `Vector{<:Integer}`が提供されると、それに対応する行と列が`f`から除外されます。`excluded === nothing`の場合、`f`の最後のインデックスが自動的に除外されます。
