```
t8_forest_get_scheme(forest)
```

フォレストに関連付けられた要素スキームを返します。

# 引数

  * `forest.`:[in] コミットされたフォレスト。

# 返り値

フォレストの要素スキーム。

# 参照

[`t8_forest_set_scheme`](@ref)

### プロトタイプ

```c
t8_scheme_cxx_t * t8_forest_get_scheme (const t8_forest_t forest);
```
