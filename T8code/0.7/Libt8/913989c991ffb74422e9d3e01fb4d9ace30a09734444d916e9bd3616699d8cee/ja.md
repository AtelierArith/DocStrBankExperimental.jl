```
t8_element_tree_face(ts, elem, face)
```

与えられた要素とこの要素の面。もし面がツリーの境界にある場合、ツリー面の面番号を返します。そうでない場合、返される値は任意です。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。
  * `face`:[in] *elem* の面のインデックス。

# 戻り値

*face* がツリーの境界にある場合、*face* のサブ面であるツリー面のインデックス。ツリーの境界にない場合は任意の整数。

### プロトタイプ

```c
int t8_element_tree_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
