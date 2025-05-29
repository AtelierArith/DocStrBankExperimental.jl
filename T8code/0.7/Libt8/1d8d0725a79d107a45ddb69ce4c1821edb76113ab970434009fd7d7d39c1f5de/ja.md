```
t8_element_get_linear_id(ts, elem, level)
```

与えられたレベルの仮想均一細分化における特定の要素の線形IDを計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] IDを計算する要素。
  * `level`:[in] 考慮すべき均一細分化のレベル。

# 戻り値

要素の線形ID。

### プロトタイプ

```c
t8_linearidx_t t8_element_get_linear_id (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int level);
```
