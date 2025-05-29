```
p8est_split_array(array, level, indices)
```

祖先の子によって四分木の配列を分割します。

レベル **level** で共通の祖先を持つ四分木のソートされた **array** を与えられたとき、レベル **level** + 1 での共通の祖先の各子の最初の四分木の **indices** を計算します。

### パラメータ

  * `array`:[in] レベル > **level** の四分木のソートされた配列。
  * `level`:[in] 共通の祖先が存在するレベル。
  * `indices`:[in,out] 祖先の各子の最初の四分木のインデックス、および末尾に追加のインデックス。**array** の子 i の子孫である四分木は、indices[i] と indices[i + 1] - 1 の間のインデックスを持ちます。もし indices[i] = indices[i+1] であれば、これは配列内に子 i に含まれる四分木がないことを示します。

### プロトタイプ

```c
void p8est_split_array (sc_array_t * array, int level, size_t indices[]);
```
