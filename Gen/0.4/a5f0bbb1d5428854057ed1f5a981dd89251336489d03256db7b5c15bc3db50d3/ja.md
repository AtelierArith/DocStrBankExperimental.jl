```
new_trace = elliptical_slice(
    trace, addr, mu, cov;
    check=false, observations=EmptyChoiceMap())
```

与えられたランダム選択に対して楕円スライスサンプリングの更新を適用します。

また、事前分布の平均ベクトルと共分散行列も受け取ります。

[Reference URL](http://proceedings.mlr.press/v9/murray10a/murray10a.pdf)
