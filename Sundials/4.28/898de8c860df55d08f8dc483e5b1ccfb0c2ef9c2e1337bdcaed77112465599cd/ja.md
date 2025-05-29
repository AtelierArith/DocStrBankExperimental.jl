```julia
IDA(;linear_solver=:Dense,jac_upper=0,jac_lower=0,krylov_dim=0,
    max_order = 5,
    max_error_test_failures = 7,
    max_nonlinear_iters = 3,
    nonlinear_convergence_coefficient = 0.33,
    nonlinear_convergence_coefficient_ic = 0.0033,
    max_num_steps_ic = 5,
    max_num_jacs_ic = 4,
    max_num_iters_ic = 10,
    max_num_backs_ic = 100,
    use_linesearch_ic = true,
    max_convergence_failures = 10,
    init_all = false,
    prec = nothing, psetup = nothing)
```

IDA: これはSundials.jlパッケージのIDAメソッドです。

### 線形ソルバー

Sundialsアルゴリズムのコンストラクタは主な引数を取ります: linearsolver - これはニュートン反復で使用される線形ソルバーです。選択肢は次の通りです:

  * :Dense - 密な線形ソルバー。
  * :Band - バンド行列のヤコビアンに特化したソルバー。使用する場合は、jac*upperおよびjac*lowerを介して上部および下部の非ゼロ対角線の位置を設定する必要があります。
  * :LapackDense - Julia提供のOpenBLASリンクされたLAPACKを使用したマルチスレッド操作のための密な線形ソルバーのバージョン。これは大規模なシステムでは:Denseよりも速いですが、小規模なシステム（<100 ODE）では顕著なオーバーヘッドがあります。
  * :LapackBand - Julia提供のOpenBLASリンクされたLAPACKを使用したマルチスレッド操作のためのバンド線形ソルバーのバージョン。これは大規模なシステムでは:Bandよりも速いですが、小規模なシステム（<100 ODE）では顕著なオーバーヘッドがあります。
  * :GMRES - GMRES法。推奨される最初の選択Krylov法。
  * :BCG - 双共役勾配法。
  * :PCG - 前処理された共役勾配法。対称線形システム専用。
  * :TFQMR - TFQMR法。
  * :KLU - スパース因子分解法。ユーザーがヤコビアンを指定する必要があります。ヤコビアンはODEProblem型でスパース行列として設定する必要があります。

反復線形ソルバーの前処理器（提供されている場合）は、左前処理器である必要があることに注意してください。

例:

```julia
IDA() # ニュートン + 密なソルバー
IDA(linear_solver=:Band,jac_upper=3,jac_lower=3) # 非ゼロ対角線3上および3下のバンドソルバー
IDA(linear_solver=:BCG) # 双共役勾配法
```

### 前処理器

ここで`prec`は（左）前処理器関数`prec(z,r,p,t,y,fy,gamma,delta)`であり、次のようになります:

  * `z`: 計算された出力ベクトル
  * `r`: 線形システムの右辺ベクトル
  * `p`: パラメータ
  * `t`: 現在の独立変数
  * `du`: `f(u,p,t)`の現在の値
  * `gamma`: `W = M - gamma*J`の`gamma`
  * `delta`: 反復法の許容誤差

`psetup`はヤコビアン情報を事前計算するための前処理器セットアップ関数です。ここで:

  * `p`: パラメータ
  * `t`: 現在の独立変数
  * `resid`: 現在の残差
  * `u`: 現在の状態
  * `du`: 現在の状態の導関数
  * `gamma`: `W = M - gamma*J`の`gamma`

`prec`が設定されている場合、`psetup`はオプションです。

### 追加オプション

追加オプションの詳細については[the Sundials manual](https://computing.llnl.gov/sites/default/files/ida_guide-5.7.0.pdf)を参照してください。オプション`init_all`は初期条件の整合性ルーチンを制御します。初期条件が不整合な場合（すなわち、暗黙の方程式を満たさない場合）、`init_all=false`は代数変数と導関数がDAEを満たすように修正されることを意味します。`init_all=true`の場合、すべての初期条件がDAEを満たすように修正されます。
