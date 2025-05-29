```
t8_element_count_leaves_from_root(ts, level)
```

与えられた均一レベルのルート要素が生成する葉の子孫の数をカウントします。

これは便利な関数であり、t8*element*count_leavesを介して実装できます。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `level`:[in] 精緻化レベル。

# 戻り値

入力要素がルート（レベル0）要素である場合のt8*element*count_leavesの値。

### プロトタイプ

```c
t8_gloidx_t t8_element_count_leaves_from_root (const t8_eclass_scheme_c *ts, int level);
```
