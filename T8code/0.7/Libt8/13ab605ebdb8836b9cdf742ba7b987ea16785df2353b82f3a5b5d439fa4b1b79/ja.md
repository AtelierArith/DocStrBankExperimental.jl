```
t8_element_compare(ts, elem1, elem2)
```

2つの要素をスキームに関して比較します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem1`:[in] 最初の要素。
  * `elem2`:[in] 2番目の要素。

# 戻り値

elem1 < elem2 の場合は負、elem1 が elem2 と等しい場合はゼロ、elem1 > elem2 の場合は正。elem2 が elem1 のコピーである場合、要素は等しいと見なされます。

### プロトタイプ

```c
int t8_element_compare (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, const t8_element_t *elem2);
```
