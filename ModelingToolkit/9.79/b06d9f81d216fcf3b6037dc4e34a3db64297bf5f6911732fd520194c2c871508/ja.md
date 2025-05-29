```julia
struct PDESystem <: ModelingToolkit.AbstractMultivariateSystem
```

偏微分方程のシステム。

# フィールド

  * `eqs`: PDEを定義する方程式。
  * `bcs`: 境界条件。
  * `domain`: 独立変数のためのドメイン。
  * `ivs`: 独立変数。
  * `dvs`: 従属変数。
  * `ps`: パラメータ。
  * `defaults`: 初期条件および/またはパラメータが`ODEProblem`に提供されていない場合に使用するデフォルト値。
  * `connector_type`: システムのタイプ。
  * `systems`: 内部システム。これらはユニークな名前を持つ必要があります。
  * `analytic`: 各従属変数の解析解の明示的な記号表現のベクトル。例: `analytic = [u(t, x) ~ a*sin(c*t) * cos(k*x)]`。
  * `analytic_func`: 各従属変数の解析解のための関数のベクトル。提供されていない場合は`analytic`から生成されます。変数と同じ引数シグネチャを持ち、最後の引数として`ps`引数を持ち、`ps`で指定した順序のパラメータ値のインデックス可能なものを受け取ります。例: `analytic_func = [u(t, x) => (ps, t, x) -> ps[1]*sin(ps[2]*t) * cos(ps[3]*x)]`。
  * `name`: システムの名前。
  * `description`: システムの説明。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUIのためのメタデータ。

# 例

```julia
using ModelingToolkit

@parameters x t
@variables u(..)
Dxx = Differential(x)^2
Dtt = Differential(t)^2
Dt = Differential(t)

#2D PDE
C=1
eq  = Dtt(u(t,x)) ~ C^2*Dxx(u(t,x))

# 初期条件と境界条件
bcs = [u(t,0) ~ 0.,# for all t > 0
       u(t,1) ~ 0.,# for all t > 0
       u(0,x) ~ x*(1. - x), #for all 0 < x < 1
       Dt(u(0,x)) ~ 0. ] #for all  0 < x < 1]

# 空間と時間のドメイン
domains = [t ∈ (0.0,1.0),
           x ∈ (0.0,1.0)]

@named pde_system = PDESystem(eq,bcs,domains,[t,x],[u])
```
