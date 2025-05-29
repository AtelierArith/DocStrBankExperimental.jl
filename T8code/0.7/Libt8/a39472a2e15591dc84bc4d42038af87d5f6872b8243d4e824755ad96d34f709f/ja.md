```
t8_element_face_shape(ts, elem, face)
```

要素の面の形状を計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。
  * `face`:[in] *elem* の面。

# 戻り値

面の要素形状。すなわち、四角形の場合は T8*ECLASS*LINE、四面体の場合は T8*ECLASS*TRIANGLE、そして面番号に応じてプリズムの場合は T8*ECLASS*QUAD または T8*ECLASS*TRIANGLE です。

### プロトタイプ

```c
t8_element_shape_t t8_element_face_shape (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
