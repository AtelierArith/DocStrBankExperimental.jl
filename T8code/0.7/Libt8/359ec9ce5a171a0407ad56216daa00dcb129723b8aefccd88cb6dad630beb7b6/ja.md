```
t8_stash_get_attribute_size(stash, index)
```

スタッシュ内の属性のサイズ（バイト単位）を返します。

# 引数

  * `stash`:[in] 考慮すべきスタッシュ。
  * `index`:[in] *stash* の属性配列内の属性のインデックス。

# 戻り値

属性のサイズ（バイト単位）。

### プロトタイプ

```c
size_t t8_stash_get_attribute_size (t8_stash_t stash, size_t index);
```
