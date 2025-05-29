```
TruncatedBSeries
```

数値積分法のB系列（空の木の係数が1である）と常微分方程式の右辺およびその摂動（空の木の係数が0である）を記述できる構造体で、指定された[`order`](@ref)まで対応しています。

一般的に、この種の`struct`は[`bseries`](@ref)またはB系列を返す他の関数（例：[`modified_equation`](@ref)や[`modifying_integrator`](@ref)）を介して構築されるべきです。
