```
plotamounts(simulation::DiscretizedSPAC)
plotamounts(simulation::DiscretizedSPAC, compartments::Symbol)
plotamounts(simulation::DiscretizedSPAC, compartments::Symbol, RWUcentroid::Symbol)
```

SPACシミュレーションの量結果をプロットします。デフォルトでは、地上および地下の両方です。ユーザーは、2番目の引数として同位体を `:aboveground`、`:belowground`、または `:above_and_belowground` のいずれかで上書きできます。RWUcentroidは、`:dontShowRWUcentroid` または `:showRWUcentroid` のいずれかの値を持つことができます。
