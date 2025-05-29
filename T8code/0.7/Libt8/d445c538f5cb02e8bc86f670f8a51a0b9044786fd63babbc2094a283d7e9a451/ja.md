```
t8_eclass_scheme_is_default(ts)
```

指定された eclass_scheme がデフォルトスキームの1つであるかどうかを確認します。

# 引数

  * `ts`:[in] スキームへのポインタ

# 戻り値

*ts* がデフォルトスキームの1つであれば真（非ゼロ）、そうでなければ偽（ゼロ）を返します。

### プロトタイプ

```c
int t8_eclass_scheme_is_default (t8_eclass_scheme_c *ts);
```
