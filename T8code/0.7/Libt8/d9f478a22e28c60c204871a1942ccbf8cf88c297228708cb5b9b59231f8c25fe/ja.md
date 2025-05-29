```
t8_element_max_num_faces(ts, elem)
```

与えられた要素とそのすべての子孫の最大面数を計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。

# 戻り値

*要素*の面の数。

### プロトタイプ

```c
int t8_element_max_num_faces (const t8_eclass_scheme_c *ts, const t8_element_t *elem);
```
