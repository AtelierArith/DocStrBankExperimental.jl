```
t8_stash_attribute_is_owned(stash, index)
```

スタッシュ内の属性がスタッシュによって所有されている場合はtrueを返します。つまり、それは[`t8_stash_add_attribute`](@ref)の呼び出しでコピーされました。属性がスタッシュによって所有されていない場合はfalseを返します。

# 引数

  * `stash`:[in] 考慮されるスタッシュ。
  * `index`:[in] *stash*の属性配列内の属性のインデックス。

# 戻り値

trueまたはfalse。

### プロトタイプ

```c
int t8_stash_attribute_is_owned (t8_stash_t stash, size_t index);
```
