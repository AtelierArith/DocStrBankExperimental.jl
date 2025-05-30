```
t8_forest_element_neighbor_eclass(forest, ltreeid, elem, face)
```

与えられた要素の隣接面にある木のeclassを返します。

# 引数

  * `forest.`:[in] 確定したフォレスト。
  * `ltreeid.`:[in] 要素が存在するローカルツリー。
  * `elem.`:[in] 木 *ltreeid* にある要素。
  * `face.`:[in] *elem* の面番号。

# 戻り値

*face* を越えた *elem* の隣接面が存在する木のローカルツリーID。

### プロトタイプ

```c
t8_eclass_t t8_forest_element_neighbor_eclass (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *elem, int face);
```
