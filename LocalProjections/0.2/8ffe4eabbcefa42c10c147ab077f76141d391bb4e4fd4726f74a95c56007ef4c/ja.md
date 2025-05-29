```
DemmlerReinsch <: SmoothAlgorithm
```

デムラー・ラインシュ直交化は、代替スムージングパラメータを用いた高速リッジ回帰のためのものです。この実装は、Ruppert et al. (2003) に従っています。

直交化が解決されると、異なるスムージングパラメータを用いた推定値を非常に低コストで生成できます。得られた推定値はモデル選択に十分な精度があり、通常は各パラメータのペナルティ付き最小二乗問題を直接解くより遅い [`DirectSolve`](@ref) アプローチによって生成された推定値に非常に近いです。

# 参考文献

Ruppert, David, M. P. Wand, M., and R. J. Carroll. 2003. Semiparametric Regression (Cambridge Series in Statistical and Probabilistic Mathematics). Cambridge: Cambridge University Press.
