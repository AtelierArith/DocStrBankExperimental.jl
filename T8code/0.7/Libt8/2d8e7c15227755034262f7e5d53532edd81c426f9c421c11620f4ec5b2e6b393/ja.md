```
t8_element_nca(ts, elem1, elem2, nca)
```

二つの要素の最近共通祖先を計算します。つまり、与えられた二つの要素を子孫として持つ最高レベルの要素です。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem1`:[in] 二つの入力要素のうちの最初の要素。
  * `elem2`:[in] 二つの入力要素のうちの二番目の要素。
  * `nca`:[in,out] この要素のストレージは存在し、子の要素クラスと一致している必要があります。出力として、**elem1** と **elem2** のユニークな最近共通祖先が得られます。

### プロトタイプ

```c
void t8_element_nca (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, const t8_element_t *elem2, t8_element_t *nca);
```
