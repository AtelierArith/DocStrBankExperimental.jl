```
unscented_transform_inverse(points::Vector{AbstractVector}, w_μ::Vector,
    w_Σ::Vector)
```

2n+1のシグマ点と重みを平均と共分散の単一の測定（GaussianBelief）に戻します。

これは、別の共分散重み付けに対するα/βパラメータのためにProbRobからの定式化を使用していますが、これは必ずしも必要ではありません。
