```
fejer1(n, [T])
```

Fejérの第一則に対する`n`個の重みを計算します。これは、0からπまでの間に均等に配置された`n`個のノードに対応します。すなわち、ノードは次の位置にあります。

$$
\theta_k = k \frac{\pi}{n-1} \quad k=0, \ldots, n-1.
$$

この関数は[Waldvogelの方法](@cite Waldvogel_2006)を使用します。

型`T`は任意の`AbstractFloat`である可能性がありますが、デフォルトは`Float64`です。 ```
