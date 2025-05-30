```
t8_element_parent(ts, elem, parent)
```

与えられた要素 **elem** の親を計算し、それを **parent** に格納します。**parent** は既存の要素である必要があります。この関数によってメモリは割り当てられません。**elem** と **parent** は同じ要素を指すことができ、その場合 **elem** のエントリは親のエントリによって上書きされます。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 親が計算される要素。
  * `parent`:[in,out] この要素のエントリは **elem** の親のエントリによって上書きされます。この要素のストレージは存在し、親の要素クラスと一致する必要があります。

### プロトタイプ

```c
void t8_element_parent (const t8_eclass_scheme_c *ts, const t8_element_t *elem, t8_element_t *parent);
```
