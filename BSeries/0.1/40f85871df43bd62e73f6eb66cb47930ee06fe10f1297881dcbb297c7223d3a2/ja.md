```
ContinuousStageRungeKuttaMethod(M)
```

連続ステージルンゲクッタ（CSRK）法を説明する構造体です。MiyatakeとButcher（2016）によって説明されたパラメータ行列`M`を渡すことで構築できます。この方法のB系列は[`bseries`](@ref)を使用して計算できます。

# 参考文献

  * Yuto Miyatake and John C. Butcher. "エネルギー保存法の特性とハミルトン系のための並列積分器の構築." SIAM Journal on Numerical Analysis 54, no. 3 (2016): [DOI: 10.1137/15M1020861](https://doi.org/10.1137/15M1020861)
