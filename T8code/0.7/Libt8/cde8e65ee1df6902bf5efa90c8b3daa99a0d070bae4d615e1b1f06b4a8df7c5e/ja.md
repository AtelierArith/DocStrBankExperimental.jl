```
t8_element_num_siblings(ts, elem)
```

要素の兄弟の数を計算します。つまり、親の子供の数です。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。

# 戻り値

*要素*の兄弟の数。要素自体も兄弟としてカウントするため、この数は >= 1 です。

### プロトタイプ

```c
int t8_element_num_siblings (const t8_eclass_scheme_c *ts, const t8_element_t *elem);
```
