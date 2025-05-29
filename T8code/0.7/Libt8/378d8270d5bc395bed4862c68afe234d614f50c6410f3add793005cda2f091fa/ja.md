```
t8_element_set_linear_id(ts, elem, level, id)
```

均一な細分化における与えられた線形IDに従って、割り当てられた要素のエントリを初期化します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in,out] エントリが設定される要素。
  * `level`:[in] 考慮すべき均一な細分化のレベル。
  * `id`:[in] 線形ID。idは0 <= id < '均一な細分化の葉の数'を満たさなければなりません。

### プロトタイプ

```c
void t8_element_set_linear_id (const t8_eclass_scheme_c *ts, t8_element_t *elem, int level, t8_linearidx_t id);
```
