```
ClimaTimeSteppers
```

常微分方程ソルバー

JuliaDiffEq用語:

  * *関数*: 右辺関数 df/dt。

      * デフォルトでは、関数は `ODEFunction` にラップされます。
      * 増分関数呼び出しをサポートする新しい `IncrementingODEFunction` を定義します。
  * *問題*: 関数、初期 u、時間範囲、パラメータおよびオプション

    `du/dt = f(u,p,t) = fL(u,p,t)  + fR(u,p,t)`

    `fR(u,p,t) == f(u.p,t) - fL(u,p,t)` `fL(u,_,_) == A*u ただし、ある`A`（行列フリー）`

    SplitODEProlem(fL, fR)
  * `ODEProblem` from SciMLBase.jl

      * 線形 + 完全 IMEX のために `ODEFunction` に `jac` オプションを使用します (https://docs.sciml.ai/latest/features/performance*overloads/#ode*explicit_jac-1)
  * 線形 + 残差 IMEX のための `SplitODEProblem`
  * 真のマルチレートのための `MultirateODEProblem`
  * *アルゴリズム*: どのアルゴリズム + オプション（例: 線形ソルバータイプ）を示す小さなオブジェクト（しばしばシングルトン）
  * 新しい抽象 `DistributedODEAlgorithm` を定義し、このパッケージのアルゴリズムはこのサブタイプになります。
  * マルチレートソルバーのための新しい `Multirate` を定義します。
  * *インテグレーター*: 解決に必要なすべてを含みます。使用方法:
  * このパッケージのソルバーのために新しい `DistributedODEIntegrator` を定義します。

    init(prob, alg, options...) => integrator   step!(int) => 単一ステップを実行   solve!(int) => 最後まで実行   solve(prob, alg, options...) => init + solve!
  * *解*（未実装）: ODEの「解」を含みます。
