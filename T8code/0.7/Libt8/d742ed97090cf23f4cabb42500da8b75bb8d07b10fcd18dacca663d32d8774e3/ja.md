```
t8_element_shape(ts, elem)
```

割り当てられた要素の形状をそのタイプに応じて返します。たとえば、要素の子は異なる形状の要素である可能性があり、その形状に応じて異なる方法で処理する必要があります。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 考慮すべき要素

# 戻り値

要素の形状をeclassとして返します。

### プロトタイプ

```c
t8_element_shape_t t8_element_shape (const t8_eclass_scheme_c *ts, const t8_element_t *elem);
```
