```
t8_forest_leaf_face_orientation(forest, ltreeid, ts, leaf, face)
```

与えられた面における葉の面の向きを計算します。

面の向きのエンコーディングに関する詳細は、t8*cmesh*get*face*neighborを参照してください。

# 引数

  * `forest`:[in] 森。有効なゴーストレイヤーを持っている必要があります。
  * `ltreeid`:[in] ローカルツリーID。
  * `ts`:[in] 要素のeclassスキーム。
  * `leaf`:[in] 森の*ltreeid*のツリー内の葉。
  * `face`:[in] 面の隣接を検索するための面のインデックス。

# 戻り値

整数としてエンコードされた面の向き。

### プロトタイプ

```c
int t8_forest_leaf_face_orientation (t8_forest_t forest, const t8_locidx_t ltreeid, const t8_eclass_scheme_c *ts, const t8_element_t *leaf, int face);
```
