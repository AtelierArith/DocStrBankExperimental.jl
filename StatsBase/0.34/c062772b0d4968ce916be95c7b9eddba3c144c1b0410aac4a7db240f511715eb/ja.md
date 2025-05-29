```
cumulant(v, k, [wv::AbstractWeights], m=mean(v))
```

実数値配列 `v` の `k` 番目の累積量を返します。オプションで重み付けベクトル `wv` と事前に計算された平均 `m` を指定できます。

`k` が `Integer` の範囲である場合、この範囲内のすべての累積量をベクトルとして返します。

この量は、低次の累積量と中心モーメントに基づく再帰的定義を使用して計算されます。

参考文献: Smith, P. J. 1995. A Recursive Formulation of the Old Problem of Obtaining Moments from Cumulants and Vice Versa. The American Statistician, 49(2), 217–218. https://doi.org/10.2307/2684642
