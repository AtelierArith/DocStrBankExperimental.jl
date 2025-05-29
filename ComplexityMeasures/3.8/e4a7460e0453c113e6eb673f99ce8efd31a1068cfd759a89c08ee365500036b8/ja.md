```
DifferentialInfoEstimator
```

すべての微分情報測定器のスーパークラスです。これらの測定器は、確率分布を明示的に推定することなく、さまざまな方法で情報測定を計算します。

各 [`DifferentialInfoEstimator`](@ref) は、関連する密度/積分を近似するための専門的な技術を使用しており、しばしば1つまたは数種類の情報測定に特化しています。たとえば、[`Kraskov`](@ref) は [`Shannon`](@ref) エントロピーを推定します。

使用法については、[`information`](@ref) を参照してください。

## 実装

  * [`KozachenkoLeonenko`](@ref).
  * [`Kraskov`](@ref).
  * [`Goria`](@ref).
  * [`Gao`](@ref).
  * [`Zhu`](@ref)
  * [`ZhuSingh`](@ref).
  * [`Lord`](@ref).
  * [`AlizadehArghami`](@ref).
  * [`Correa`](@ref).
  * [`Vasicek`](@ref).
  * [`Ebrahimi`](@ref).
  * [`LeonenkoProzantoSavani`](@ref).
