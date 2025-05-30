```
t8_element_face_parent_face(ts, elem, face)
```

要素の面を考慮して、要素の親の面番号を返します。要素の面と一致する親の面がない場合は-1を返します。

!!! note
    ルート要素の場合、この関数は常に*face*を返します。


# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。
  * `face`:[in] 面の番号。

# 戻り値

*elem*の*face*が*elem*の親の面でもある場合、この面の面番号を返します。そうでない場合は-1を返します。

### プロトタイプ

```c
int t8_element_face_parent_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
