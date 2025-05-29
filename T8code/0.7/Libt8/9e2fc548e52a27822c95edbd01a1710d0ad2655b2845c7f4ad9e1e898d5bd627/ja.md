```
t8_element_shape_compare(element_shape1, element_shape2)
```

同じ次元の2つの要素形状を比較し、面隣接の向きに必要な場合。実装された順序は、2Dでは三角形 < 正方形、3Dでは四面体 < 六面体 < プリズム < ピラミッドです。

# 引数

  * `element_shape1`:[in] 比較する最初の要素形状。
  * `element_shape2`:[in] 比較する2番目の要素形状。

# 戻り値

要素形状が等しい場合は0、element*shape1 > element*shape2 の場合は1、element*shape1 < element*shape2 の場合は-1を返します。

### プロトタイプ

```c
int t8_element_shape_compare (t8_element_shape_t element_shape1, t8_element_shape_t element_shape2);
```
