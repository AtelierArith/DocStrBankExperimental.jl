```
t8_element_count_leaves(ts, t, level)
```

与えられた均一レベルの要素が生成する葉の子孫の数をカウントします。

例: *t* が各レベルで2つの線要素に細分化される線要素である場合、戻り値は max(0, 2^{*level* - level(*t*)}) です。したがって、*t* のレベルが0で、*level* = 3の場合、戻り値は 2^3 = 8 です。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `t`:[in] チェックする要素。
  * `level`:[in] 細分化レベル。

# 戻り値

*t* がレベル *level* まで均一に細分化されていると仮定します。戻り値は（指定されたレベルの）結果として得られる要素の数です。もし *level* < [`t8_element_level`](@ref)(t) の場合、戻り値は0であるべきです。

### プロトタイプ

```c
t8_gloidx_t t8_element_count_leaves (const t8_eclass_scheme_c *ts, const t8_element_t *t, int level);
```
