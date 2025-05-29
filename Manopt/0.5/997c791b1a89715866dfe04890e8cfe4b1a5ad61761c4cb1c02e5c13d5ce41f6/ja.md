```
ManifoldConstrainedSetObjective{E, MO, PF, IF} <: AbstractManifoldObjective{E}
```

制約された目的関数を集合に制限してモデル化します

$$
\operatorname*{arg\,min}_{p ∈ \mathcal C} f(p)
$$

ここで、$\mathcal C ⊂ \mathcal M$ は凸閉部分集合です。

# フィールド

  * `objective::AbstractManifoldObjective` (制約のない) 目的関数で、$f$ とその勾配 $\operatorname{grad} f$ を含みます。
  * `project!!::PF` 集合 $\mathcal C$ に射影する関数 $\operatorname{proj}_{\mathcal C}: \mathcal M → \mathcal C$ です。
  * `indicator::IF` 指示関数 ``ι_{\mathcal C}(p) = \begin{cases}   0 &\text{ for }p∈\mathcal C\    ∞ &\text{ else.}\end{cases}

# コンストラクタ

```
ManifoldConstrainedSetObjective(f, grad_f, project!!; kwargs...)
```

与えられた関数 `f`、その勾配 `grad_f`、および射影 `project!!` $\operatorname{proj}_{\mathcal C}$ に対して制約された目的関数を生成します。

## キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref））を指定します。通常、最初の引数は多様体であり、修正された引数は2番目のものです。
  * `indicator=nothing`: 指示関数 $ι_{\mathcal C}(p)$。提供されない場合、射影が同じ点を返すかどうかのテストが行われます。[`InplaceEvaluation`](@ref) の場合、これには1回の割り当てが必要です。
