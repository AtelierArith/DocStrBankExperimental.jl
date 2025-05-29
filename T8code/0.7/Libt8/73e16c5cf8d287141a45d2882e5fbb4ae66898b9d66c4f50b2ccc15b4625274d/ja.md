```
t8_element_equal(ts, elem1, elem2)
```

2つの要素が等しいかどうかを確認します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem1`:[in] 最初の要素。
  * `elem2`:[in] 2番目の要素。

# 戻り値

要素が等しい場合は1、等しくない場合は0

### プロトタイプ

```c
int t8_element_equal (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, const t8_element_t *elem2);
```
