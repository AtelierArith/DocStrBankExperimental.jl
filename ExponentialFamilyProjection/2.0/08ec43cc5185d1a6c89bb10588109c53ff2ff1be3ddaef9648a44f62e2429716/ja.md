```
project_to(to::ProjectedTo, argument::F, supplementary..., initialpoint, kwargs...)
```

`argument`の最も近い投影を`to`で指定された指数族分布に見つけます。

# 引数

  * `to::ProjectedTo`: 投影の設定。詳細については`ProjectedTo`を参照してください。
  * `argument::F`: 任意の分布の対数PDFを表す（正規化されていない）関数*または*サンプルのリスト。
  * `supplementary...`: `argument`とこれらの分布の積を投影するための追加の分布（オプション）。
  * `initialpoint`: 最適化プロセスの開始点（オプション）。
  * `kwargs...`: `Manopt.gradient_descent!`に渡される追加の引数（オプション）。`gradient_descent!`のパラメータの詳細については、[Manopt.jlのドキュメント](https://manoptjl.org/stable/solvers/gradient_descent/#Manopt.gradient_descent)を参照してください。

# 補足

`supplementary`分布は、`to`で指定されたターゲット分布の型と条件に一致する必要があります。補足分布を含めることは、次のように`argument`関数を修正することに相当します：

```julia
f_modified = (x) -> argument(x) + logpdf(supplementary[1], x) + logpdf(supplementary[2], x) + ...
```

```jldoctest
julia> using ExponentialFamily, BayesBase

julia> f = (x) -> logpdf(Beta(30.14, 2.71), x);

julia> prj = ProjectedTo(Beta; parameters = ProjectionParameters(niterations = 500))
ProjectedTo(Beta)

julia> project_to(prj, f) isa ExponentialFamily.Beta
true
```

```jldoctest
julia> using ExponentialFamily, BayesBase, StableRNGs

julia> samples = rand(StableRNG(42), Beta(30.14, 2.71), 1_000);

julia> prj = ProjectedTo(Beta; parameters = ProjectionParameters(tolerance = 1e-2))
ProjectedTo(Beta)

julia> project_to(prj, samples) isa ExponentialFamily.Beta
true
```

!!! note
    異なる戦略は異なるタイプの引数と互換性があります。詳細については、ドキュメントの最適化戦略セクションをお読みください。


```
