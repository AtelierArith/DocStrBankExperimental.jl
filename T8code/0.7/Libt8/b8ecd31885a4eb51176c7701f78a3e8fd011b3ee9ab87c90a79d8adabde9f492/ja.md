```
t8_stash_get_attribute(stash, index)
```

スタッシュ内の属性へのポインタを返します。

# 引数

  * `stash`:[in] 考慮されるスタッシュ。
  * `index`:[in] *stash* の属性配列内の属性のインデックス。

# 戻り値

属性が格納されているメモリ領域への void ポインタ。

### プロトタイプ

```c
void * t8_stash_get_attribute (t8_stash_t stash, size_t index);
```
