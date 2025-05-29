```julia
CVODE_BDF(;method=:Newton,linear_solver=:Dense,
          jac_upper=0,jac_lower=0,
          stored_upper = jac_upper + jac_lower,
          non_zero=0,krylov_dim=0,
          stability_limit_detect=false,
          max_hnil_warns = 10,
          max_order = 5,
          max_error_test_failures = 7,
          max_nonlinear_iters = 3,
          max_convergence_failures = 10,
          prec = nothing, prec_side = 0)
```

CVODE_BDF: CVode 後方差分法 (BDF) ソルバー。

### メソッドの選択肢

  * method - これは暗黙の方程式を解くためのメソッドです。BDFの場合、デフォルトは :Newton で、Adamsの場合は :Functional です。これらの選択肢は、Sundials.jl マニュアルで推奨されるペアリングに一致します。ただし、:Newton メソッドを使用すると、反復回数は少なくて済むかもしれませんが、:Function 反復アプローチよりも多くのメモリを必要とします。
  * linear_solver - これは :Newton メソッドで使用される線形ソルバーです。

### 線形ソルバーの選択肢

線形ソルバーの選択肢は次のとおりです：

  * :Dense - 密な線形ソルバー。
  * :Band - 帯状ヤコビアンに特化したソルバー。使用する場合は、jac*upper と jac*lower を介して上部および下部の非ゼロ対角線の位置を設定する必要があります。
  * :LapackDense - Julia 提供の OpenBLAS にリンクされた LAPACK を使用してマルチスレッド操作を行う密な線形ソルバーのバージョン。これは大規模なシステムでは :Dense よりも高速ですが、小規模な (<100 ODE) システムでは顕著なオーバーヘッドがあります。
  * :LapackBand - Julia 提供の OpenBLAS にリンクされた LAPACK を使用してマルチスレッド操作を行う帯状線形ソルバーのバージョン。これは大規模なシステムでは :Band よりも高速ですが、小規模な (<100 ODE) システムでは顕著なオーバーヘッドがあります。
  * :Diagonal - このメソッドは対角ヤコビアンに特化しています。
  * :GMRES - GMRES メソッド。最初の選択肢として推奨される Krylov メソッド。
  * :BCG - 双共役勾配法。
  * :PCG - 前処理された共役勾配法。対称線形システム専用。
  * :TFQMR - TFQMR メソッド。
  * :KLU - スパース因子分解法。ユーザーがヤコビアンを指定する必要があります。ヤコビアンは ODEProblem 型でスパース行列として設定する必要があります。

例：

```julia
CVODE_BDF() # Newton + Dense ソルバーを使用した BDF メソッド
CVODE_BDF(method=:Functional) # Functional 反復を使用した BDF メソッド
CVODE_BDF(linear_solver=:Band,jac_upper=3,jac_lower=3) # 非ゼロ対角線が上に3、下に3の帯状ソルバー
CVODE_BDF(linear_solver=:BCG) # 双共役勾配法
```

### 前処理器

ここで `prec` は前処理器関数 `prec(z,r,p,t,y,fy,gamma,delta,lr)` であり、次のようになります：

  * `z`: 計算された出力ベクトル
  * `r`: 線形システムの右辺ベクトル
  * `p`: パラメータ
  * `t`: 現在の独立変数
  * `du`: 現在の `f(u,p,t)` の値
  * `gamma`: `W = M - gamma*J` の `gamma`
  * `delta`: 反復法の許容誤差
  * `lr`: `lr=1`（左）または `lr=2`（右）前処理のフラグ

また、`psetup` はヤコビアン情報を事前計算するための前処理器セットアップ関数 `psetup(p, t, u, du, jok, jcurPtr, gamma)` です。ここで：

  * `p`: パラメータ
  * `t`: 現在の独立変数
  * `u`: 現在の状態
  * `du`: 現在の `f(u,p,t)`
  * `jok`: ヤコビアンを更新する必要があるかどうかを示すブール値
  * `jcurPtr`: ヤコビアンが更新されたかどうかを示す Int への参照。ヤコビアンが更新された場合は `jcurPtr[]=true` を設定し、更新されなかった場合は `jcurPtr[]=false` を設定する必要があります。
  * `gamma`: `W = M - gamma*J` の `gamma`

`prec` が設定されている場合、`psetup` はオプションです。

### 追加オプション

追加のオプションの詳細については、[CVODE マニュアル](https://computing.llnl.gov/sites/default/files/cv_guide-5.7.0.pdf)を参照してください。
