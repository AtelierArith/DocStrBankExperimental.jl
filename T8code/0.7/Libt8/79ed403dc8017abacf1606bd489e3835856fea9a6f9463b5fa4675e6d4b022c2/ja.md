```
t8_element_child(ts, elem, childid, child)
```

指定された番号の子要素を構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] これは有効な要素でなければならず、maxlevel より大きい必要があります。
  * `childid`:[in] 構築する子の番号。
  * `child`:[in,out] この要素のストレージは存在する必要があります。出力時には、有効な要素です。elem = child でこの関数を呼び出すことは有効です。

### プロトタイプ

```c
void t8_element_child (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int childid, t8_element_t *child);
```
