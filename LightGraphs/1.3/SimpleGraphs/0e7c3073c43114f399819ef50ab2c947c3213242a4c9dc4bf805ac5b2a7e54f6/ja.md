```
grid(dims; periodic=false)
```

$$
|dims|
$$

次元の立方格子を作成し、次元$i$における長さは`dims[i]`です。

### オプション引数

  * `periodic=false`: trueの場合、結果の格子は各次元において周期境界条件を持ちます。

# 例

```jldoctest
julia> grid([2,3])
{6, 7} 無向単純Int64グラフ

julia> grid(Int8[2, 2, 2], periodic=true)
{8, 12} 無向単純Int8グラフ

julia> grid((2,3))
{6, 7} 無向単純Int64グラフ
```
