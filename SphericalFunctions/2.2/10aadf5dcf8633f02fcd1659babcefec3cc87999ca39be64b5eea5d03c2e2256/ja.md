```
clenshaw_curtis(n, [T])
```

`n` の重みを Clenshaw-Curtis ルールに対して計算し、0 から π までの間に均等に配置された `n` のノードに対応します。すなわち、ノードは次の位置にあります。

$$
\theta_k = k \frac{\pi}{n-1} \quad k=0, \ldots, n-1.
$$

この関数は [Waldvogel's method](@cite Waldvogel_2006) を使用します。

型 `T` は任意の `AbstractFloat` である可能性がありますが、デフォルトは `Float64` です。 ```
