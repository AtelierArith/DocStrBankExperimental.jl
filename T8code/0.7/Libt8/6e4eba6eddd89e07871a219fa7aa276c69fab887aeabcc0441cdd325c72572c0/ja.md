```
t8_element_ancestor_id(ts, elem, level)
```

要素の祖先IDを計算します。これは、指定されたレベルでの子IDです。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] これは有効な要素でなければなりません。
  * `level`:[in] 精緻化レベル。*level* < elem.levelを満たす必要があります。

# 戻り値

*elem*の*level*祖先に関するchild_id。

### プロトタイプ

```c
int t8_element_ancestor_id (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int level);
```
