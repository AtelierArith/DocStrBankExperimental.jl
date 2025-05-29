```
t8_eclass_compare(eclass1, eclass2)
```

同じ次元の2つのeclassを比較し、面の隣接方向に必要なものです。実装された順序は、2Dでは三角形 < 正方形、3Dでは四面体 < 六面体 < プリズム < ピラミッドです。

# 引数

  * `eclass1`:[in] 比較する最初のeclass。
  * `eclass2`:[in] 比較する2番目のeclass。

# 戻り値

eclassが等しい場合は0、eclass1 > eclass2の場合は1、eclass1 < eclass2の場合は-1を返します。

### プロトタイプ

```c
int t8_eclass_compare (t8_eclass_t eclass1, t8_eclass_t eclass2);
```
