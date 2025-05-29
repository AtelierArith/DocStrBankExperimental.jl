```
det_given_divisor(x::ZZMatrix, d::ZZRingElem, proved=true)
```

行列 $x$ の行列式の正の約数が与えられたとき、その行列式を返します。`proved == true`（デフォルト）であれば、出力は正しいことが保証されます。そうでない場合は、ヒューリスティックアルゴリズムが使用されます。
