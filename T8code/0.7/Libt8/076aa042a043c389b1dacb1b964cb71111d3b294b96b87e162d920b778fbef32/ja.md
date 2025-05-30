```
t8_element_children(ts, elem, length, c)
```

与えられた要素のすべての子を構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] これは有効な要素でなければならず、maxlevelより大きい必要があります。
  * `length`:[in] 出力配列 *c* の長さは子の数と一致しなければなりません。
  * `c`:[in,out] これらの *length* 要素のストレージは存在し、子の順序における要素クラスと一致しなければなりません。出力時には、すべての子が有効です。elem = c[0] でこの関数を呼び出すことは有効です。

# 参照

[`t8_element_num_children`](@ref)

### プロトタイプ

```c
void t8_element_children (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int length, t8_element_t *c[]);
```
