```
t8_element_first_descendant(ts, elem, desc, level)
```

与えられた要素の最初の子孫を計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 子孫が計算される要素。
  * `desc`:[out] 最大可能レベルの*elem*の均一な細分化における最初の要素。

### プロトタイプ

```c
void t8_element_first_descendant (const t8_eclass_scheme_c *ts, const t8_element_t *elem, t8_element_t *desc, int level);
```
