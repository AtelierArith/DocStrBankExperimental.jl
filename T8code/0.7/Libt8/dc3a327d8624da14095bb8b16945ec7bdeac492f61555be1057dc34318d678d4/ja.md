```
t8_element_copy(ts, source, dest)
```

**source**のすべてのエントリを**dest**にコピーします。**dest**は既存の要素でなければなりません。この関数によってメモリは割り当てられません。

!!! note
    *source* と *dest* は同じ要素を指す場合があります。


# 引数

  * `ts`:[in] クラススキームの実装。
  * `source`:[in] **dest**にコピーされるエントリを持つ要素。
  * `dest`:[in,out] この要素のエントリは**source**のエントリで上書きされます。

### プロトタイプ

```c
void t8_element_copy (const t8_eclass_scheme_c *ts, const t8_element_t *source, t8_element_t *dest);
```
