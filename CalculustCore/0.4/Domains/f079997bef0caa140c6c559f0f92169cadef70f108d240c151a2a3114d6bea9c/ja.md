```julia
UnitBoxDomain(D; kwargs...)

```

`0.0`と`1.0`の端点を持つ`D`次元の単位サイズのボックスドメインを作成します。

# キーワード引数

  * `periodic_dims`: `1:D`の周期的次元のリスト。デフォルトではなし。
  * `tag`: ドメインタグ（シンボル）、デフォルトは`:Interior`。
  * `boundary_tags`: `2D`境界タグのリスト。デフォルトでは、周期的境界は`:Dk_periodic`でタグ付けされ、ここで`k`は`k`次元を指し、非周期的境界は`k`次元の下限と上限に対応して`:Dk_inf`、`:Dk_sup`としてタグ付けされます。
