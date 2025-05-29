```julia
BoxDomain(endpoints; periodic_dims, tag, boundary_tags)

```

`endpoints`で与えられた`D`次元のボックスドメインを作成します。

# キーワード引数

  * `periodic_dims`: `1:D`の周期的次元のリスト。デフォルトはなし。
  * `tag`: ドメインタグ（シンボル）、デフォルトは`:Interior`。
  * `boundary_tags`: `2D`境界タグのリスト。デフォルトでは、周期的境界は`:Dk_periodic`でタグ付けされ、ここで`k`は`k`次元を指し、非周期的境界は`k`次元の下限と上限に対応して`:Dk_inf`、`:Dk_sup`としてタグ付けされます。

# 例

```
julia> domain = BoxDomain(0, 1, 2, 3; periodic_dims=2)
(0, 1) × (2, 3)

julia> boundary_tags(domain)
(:D1_inf, :D1_sup, :D2_periodic, :D2_periodic)
```
