```
t8_element_boundary_face(ts, elem, face, boundary, boundary_scheme)
```

特定の面で境界要素を構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 入力要素。
  * `face`:[in] 境界要素を構築する面のインデックス。
  * `boundary`:[in,out] *element* より次元が1少ないように割り当てられた要素。エントリは *element* の面のエントリで埋められます。
  * `boundary_scheme`:[in] 境界面の eclass のスキーム。*elem* が T8*ECLASS*VERTEX のクラスである場合、*boundary* は NULL でなければならず、変更されません。

### プロトタイプ

```c
void t8_element_boundary_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *boundary, const t8_eclass_scheme_c *boundary_scheme);
```
