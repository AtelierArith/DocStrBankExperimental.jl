```
t8_element_num_face_children(ts, elem, face)
```

要素が細分化されるときの要素の面の子供の数を計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。
  * `face`:[in] *elem* の面。

# 戻り値

*elem* が細分化される場合の *face* の子供の数。

### プロトタイプ

```c
int t8_element_num_face_children (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
