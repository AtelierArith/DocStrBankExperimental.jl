```
p8est_lid_init(input, high, low)
```

指定された値に線形インデックスを初期化します。

### パラメータ

  * `a`:[in,out] 初期化される[`p8est_lid_t`](@ref)へのポインタ。
  * `high`:[in] *a*を初期化するための指定された高ビット。
  * `low`:[in] *a*を初期化するための指定された低ビット。

### プロトタイプ

```c
void p8est_lid_init (p8est_lid_t * input, uint64_t high, uint64_t low);
```
