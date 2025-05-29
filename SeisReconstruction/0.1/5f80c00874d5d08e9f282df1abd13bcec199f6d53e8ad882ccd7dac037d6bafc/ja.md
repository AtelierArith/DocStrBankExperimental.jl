```
ConjugateGradients(d,operators,parameters;<keyword arguments>)
```

スケールズ（1987）のアルゴリズム2に従った共役勾配法。ユーザーは線形演算子の配列を提供します。線形演算子が内積を通過することを確認してください。詳細については、[`DotTest`](@ref)を参照してください。

# 引数

  * `Niter=10` : イテレーションの数
  * `mu=0`
  * `tol=1.0e-15`
