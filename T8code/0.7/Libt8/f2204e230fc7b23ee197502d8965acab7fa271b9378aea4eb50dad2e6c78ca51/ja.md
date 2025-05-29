```
t8_element_sibling(ts, elem, sibid, sibling)
```

与えられた要素 **elem** の特定の兄弟を計算し、それを **sibling** に格納します。**sibling** は既存の要素である必要があります。この関数によってメモリは割り当てられません。**elem** と **sibling** は同じ要素を指すことができ、その場合、**elem** のエントリはその i 番目の兄弟のエントリによって上書きされます。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 兄弟が計算される要素。
  * `sibid`:[in] 計算された兄弟の ID。
  * `sibling`:[in,out] この要素のエントリは **elem** の sibid 番目の兄弟のエントリによって上書きされます。この要素のストレージは存在し、兄弟の要素クラスと一致している必要があります。

### プロトタイプ

```c
void t8_element_sibling (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int sibid, t8_element_t *sibling);
```
