```
bootstrap(lmm::LMM; double = false, n = 100, verbose = true, init = lmm.result.theta, rng = default_rng())
```

パラメトリックブートストラップ。

!!! 警告     実験的: APIは安定していません

  * double - ダブルアプローチを使用する（デフォルト - false）;
  * n - ブートストラップサンプルの数;
  * verbose - 進行状況バーを表示する;
  * init - lmmの初期値;
  * rng - 擬似乱数生成器。

パラメトリックブートストラップは、フィッティングされたLMMモデルから与えられた既知の分布からランダムな応答ベクトルを生成することに基づいています。

  * シンプルブートストラップ:

一段階のブートストラップでは、分散パラメータと係数が一度のステップでシミュレートされます。  

  * ダブルブートストラップ:

ダブルブートストラップ（二段階）では、最初のサイクルで分散パラメータがシミュレートされ、その後、係数とvar(β)のシミュレーションに使用されます。第二段階では、親モデルβがシミュレーションに使用されます。 

```julia
lmm = Metida.LMM(@formula(var~sequence+period+formulation), df0m;
random = Metida.VarEffect(Metida.@covstr(formulation|subject), Metida.CSH),
)
Metida.fit!(lmm)
bt = Metida.bootstrap(lmm; n = 1000, double = true, rng = MersenneTwister(1234))
confint(bt)
```

参照: [`confint`](@ref), [`Metida.miboot`](@ref), [`Metida.nvar`](@ref), [`Metida.tvar`](@ref),  [`Metida.straps`](@ref), [`Metida.sdstraps`](@ref), [`Metida.thetastraps`](@ref)
