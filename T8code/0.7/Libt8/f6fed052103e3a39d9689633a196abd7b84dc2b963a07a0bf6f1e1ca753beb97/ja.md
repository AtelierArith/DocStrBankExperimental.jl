```
t8_forest_element_face_neighbor(forest, ltreeid, elem, neigh, neigh_scheme, face, neigh_face)
```

要素の面隣接を構築します。ツリーの境界を越える可能性があります。隣接要素が存在するツリーのグローバルツリーIDを返します。

# 引数

  * `elem`:[in] 考慮される要素。
  * `neigh`:[in,out] 入力時には面隣接のeclassのスキームの割り当てられた要素。出力時には、この要素のデータが面隣接のデータで埋められます。隣接が存在しない場合、データは任意に変更される可能性があります。
  * `neigh_scheme`:[in] *neigh* のeclassスキーム。
  * `face`:[in] 隣接が構築されるべき面の番号。
  * `neigh_face`:[out] *neigh* の視点から見た面の番号。

# 戻り値

*neigh* が存在するツリーのグローバルツリーID。隣接がその面を越えて存在しない場合は -1。

### プロトタイプ

```c
t8_gloidx_t t8_forest_element_face_neighbor (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *elem, t8_element_t *neigh, t8_eclass_scheme_c *neigh_scheme, int face, int *neigh_face);
```
