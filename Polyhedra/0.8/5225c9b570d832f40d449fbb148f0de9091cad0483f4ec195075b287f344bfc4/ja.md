```
vrep(lines::LineIt, rays::RayIt; d::FullDim)
```

次元 `d` の全次元の多面体円錐の V 表現を作成します。これは、線 `lines` と光線 `rays` の円錐包に等しいです。

### 例

```julia
vrep([Line([0, 1])], [Ray([1, 0])])
```

半空間 $x_1 \ge 0$ の V 表現を作成します。 ```
