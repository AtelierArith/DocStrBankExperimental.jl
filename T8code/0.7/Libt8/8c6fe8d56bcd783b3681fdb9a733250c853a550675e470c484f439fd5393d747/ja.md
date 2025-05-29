```
t8_forest_get_eclass(forest, ltreeid)
```

フォレストのローカルツリーの要素クラスを返します。

# 引数

  * `forest`:[in] フォレスト。
  * `ltreeid`:[in] *forest*内のツリーのローカルID。

# 戻り値

ツリー*ltreeid*の要素クラス。*forest*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_eclass_t t8_forest_get_eclass (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
