```
t8_element_successor(ts, elem1, elem2)
```

与えられた要素の後継を一様な細分化で構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem1`:[in] 後継を構築する要素。
  * `elem2`:[in,out] エントリが設定される要素。
  * `level`:[in] 考慮すべき一様な細分化のレベル。

### プロトタイプ

```c
void t8_element_successor (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, t8_element_t *elem2);
```
