```
fejer2(n, [T])
```

`n` 個の重みを計算します。これは、0 と π の間に均等に配置された `n` 個のノードに対応します。すなわち、ノードは次の位置にあります。

$$
\theta_k = k \frac{\pi}{n+1} \quad k=1, \ldots, n.
$$

この関数は [Waldvogelの方法](@cite Waldvogel_2006) を使用します。しかし、Waldvogel の表記法とは異なり、このルーチンは ϑ=0 または π のノードに対応する重みを *含まない* ことに注意してください。これらのノードはどちらも重み 0 です。

型 `T` は任意の `AbstractFloat` である可能性がありますが、デフォルトは `Float64` です。
