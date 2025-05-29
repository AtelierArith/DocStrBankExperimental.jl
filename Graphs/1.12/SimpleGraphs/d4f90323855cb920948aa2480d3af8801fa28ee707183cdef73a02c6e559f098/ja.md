```
double_binary_tree(k::Integer)
```

`k` レベルの二重完全二分木を作成します。

### 参考文献

  * Guattery と Miller による 1998 年のスペクトルクラスタリングの例として使用されました。

# 例

```jldoctest
julia> using Graphs

julia> double_binary_tree(4)
{30, 29} 無向単純 Int64 グラフ

julia> double_binary_tree(Int8(5))
{62, 61} 無向単純 Int8 グラフ
```
