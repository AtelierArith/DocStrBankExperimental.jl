```
FixedPointAccelerationJL(;
    algorithm = :Anderson, m = missing, condition_number_threshold = missing,
    extrapolation_period = missing, replace_invalids = :NoAction
)
```

[FixedPointAcceleration.jl](https://s-baumann.github.io/FixedPointAcceleration.jl/) のラッパーで、固定点問題を解決します。このアルゴリズムを使用して根を見つける問題を解決することも許可されています。

### キーワード引数

  * `algorithm`: 使用するアルゴリズム。`：Anderson`、`：MPE`、`：RRE`、`：VEA`、`：SEA`、`：Simple`、`：Aitken` または `：Newton` のいずれか。
  * `m`: 外挿に使用する以前の反復の数。`：Anderson` のみ有効。
  * `condition_number_threshold`: 最小二乗問題の条件数の閾値。`：Anderson` のみ有効。
  * `extrapolation_period`: 外挿の間の反復の数。`：MPE`、`：RRE`、`：VEA` および `：SEA` のみ有効。`：MPE` と `：RRE` のデフォルトは `7`、`：SEA` と `：VEA` のデフォルトは `6`。`：SEA` と `：VEA` では、これは `2` の倍数でなければなりません。
  * `replace_invalids`: 無効な反復を置き換えるために使用する方法。`：ReplaceInvalids`、`：ReplaceVector` または `：NoAction` のいずれか。

!!! note
    このアルゴリズムは `FixedPointAcceleration.jl` がインストールされ、ロードされている場合にのみ利用可能です。

