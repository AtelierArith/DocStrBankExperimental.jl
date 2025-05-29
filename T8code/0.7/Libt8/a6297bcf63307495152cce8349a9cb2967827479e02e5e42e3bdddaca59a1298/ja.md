```
t8_element_extrude_face(ts, face, face_scheme, elem, root_face)
```

ルートツリーの面内にある境界面を考慮して、与えられた面を持つルートツリー内の要素を構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `face`:[in] 面要素。
  * `face_scheme`:[in] 面要素のスキーム。
  * `elem`:[in,out] 割り当てられた要素。エントリは、*face* を面として持ち、ルートツリー内にある要素のデータで埋められます。
  * `root_face`:[in] *face* が存在するルートツリーの面のインデックス。

# 戻り値

*face* と一致する *elem* の面番号。

### プロトタイプ

```c
int t8_element_extrude_face (const t8_eclass_scheme_c *ts, const t8_element_t *face, const t8_eclass_scheme_c *face_scheme, t8_element_t *elem, int root_face);
```
