```
t8_element_get_face_corner(ts, elem, face, corner)
```

要素の面のコーナーの番号を返します。例の四角形: 2 x –- x 3 | | | | 面 1 0 x –- x 1 したがって、face = 1 の場合、出力は次のとおりです: corner=0 : 1, corner=1: 3

コーナーを指定する順序は、*element* の eclass によって決まります: LINE/QUAD/TRIANGLE: 特定の順序なし。HEX : 最も低いコーナー番号から始まる面の Z-順序。TET : 要素の「外側」から見て、最も低いコーナー番号から反時計回りに始まります。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `element`:[in] 要素。
  * `face`:[in] *element* の面インデックス。
  * `corner`:[in] 面のコーナーインデックス 0 <= *corner* < num*face*corners。

# 戻り値

*face* の *corner*-番目の頂点のコーナー番号。

### プロトタイプ

```c
int t8_element_get_face_corner (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, int corner);
```
