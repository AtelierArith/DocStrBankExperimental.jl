```
t8_forest_get_eclass_scheme(forest, eclass)
```

与えられた要素クラスに関連付けられた森林のeclassスキームを返します。

!!! note
    森林は*eclass*クラスの木を持つ必要はありません。


# 引数

  * `forest.`:[in] コミットされた森林。
  * `eclass.`:[in] 要素クラス。

# 返り値

森林に関連付けられた*eclass*のeclassスキーム。

# 参照

[`t8_forest_set_scheme`](@ref)

### プロトタイプ

```c
t8_eclass_scheme_c * t8_forest_get_eclass_scheme (t8_forest_t forest, t8_eclass_t eclass);
```
