```
ttm(X,M[,modes,t='n'])
ttm(X::ttensor,M[,modes,t='n'])
```

テンソルと行列の積 (nモード積):  X x₁ M₁ x₂ M₂ x₃ ⋯ xₙ Mₙ デフォルトモード: 1:length(M)。 t='t' の場合、Mから行列を転置します。
