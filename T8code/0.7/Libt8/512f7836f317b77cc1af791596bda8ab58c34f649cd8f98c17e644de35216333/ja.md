```
t8_element_get_corner_face(ts, elem, corner, face)
```

要素のコーナーを共有する面の番号を計算します。例の四角形: 2 x –- x 3 | | | | 面 1 0 x –- x 1 面 2 したがって、corner = 1 の場合、出力は次のようになります: face=0 : 2, face=1: 1

# 引数

  * `ts`:[in] クラススキームの実装。
  * `element`:[in] 要素。
  * `corner`:[in] 面のコーナーインデックス。
  * `face`:[in] *corner* の面インデックス。

# 戻り値

*corner* での *face*-番目の面の面番号。

### プロトタイプ

```c
int t8_element_get_corner_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int corner, int face);
```
