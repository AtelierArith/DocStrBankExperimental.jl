```
t8_element_is_family(ts, fam)
```

与えられた要素のセットがファミリーであるかどうかを照会します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `fam`:[in] クラス **ts** の要素が持つ子要素と同じ数の要素を持つ配列。

# 戻り値

**fam** がファミリーでない場合はゼロ、ファミリーである場合は非ゼロを返します。

### プロトタイプ

```c
int t8_element_is_family (const t8_eclass_scheme_c *ts, t8_element_t *const *fam);
```
