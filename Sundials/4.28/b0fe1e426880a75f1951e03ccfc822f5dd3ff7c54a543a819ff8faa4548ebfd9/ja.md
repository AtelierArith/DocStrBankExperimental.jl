```julia
ARKODE(stiffness=Sundials.Implicit();
      method=:Newton,linear_solver=:Dense,
      jac_upper=0,jac_lower=0,stored_upper = jac_upper+jac_lower,
      non_zero=0,krylov_dim=0,
      max_hnil_warns = 10,
      max_error_test_failures = 7,
      max_nonlinear_iters = 3,
      max_convergence_failures = 10,
      predictor_method = 0,
      nonlinear_convergence_coefficient = 0.1,
      dense_order = 3,
      order = 4,
      set_optimal_params = false,
      crdown = 0.3,
      dgmax = 0.2,
      rdiv = 2.3,
      msbp = 20,
      adaptivity_method = 0,
      prec = nothing, psetup = nothing, prec_side = 0
      )
```

ARKODE: オプションの選択に応じて、2-8次の明示的およびESDIRKルンゲ・クッタ法。

### タブローの選択

ARKODEの主なオプションは、明示的と暗黙的の選択と、次の方法の順序です。

ARKODE(Sundials.Explicit()) # デフォルトの4次の明示的タブローで解く ARKODE(Sundials.Implicit(),order = 3) # 3次の明示的タブローで解く

明示的な順序の選択は2から8まで、暗黙的な順序は3から5までです。特定の方法は、明示的および暗黙的タブローそれぞれのetableおよびitableオプションを通じて設定することもできます。利用可能なタブローは次のとおりです。

etable:

  * HEUN*EULER*2*1*2: 2次のヘインの方法
  * BOGACKI*SHAMPINE*4*2*3:
  * ARK324L2SA*ERK*4*2*3: ケネディとカーペンターの3次法の明示的部分
  * ZONNEVELD*5*3_4: 4次の明示的手法
  * ARK436L2SA*ERK*6*3*4: ケネディとカーペンターの4次法の明示的部分
  * SAYFY*ABURUB*6*3*4: 4次の明示的手法
  * CASH*KARP*6*4*5: 5次の明示的手法
  * FEHLBERG*6*4_5: フェールベルグの古典的な5次法
  * DORMAND*PRINCE*7*4*5: 古典的な5次のドーマンド・プリンス法
  * ARK548L2SA*ERK*8*4*5: ケネディとカーペンターの5次法の明示的部分
  * VERNER*8*5_6: ヴェルナーの古典的な5次法
  * FEHLBERG*13*7_8: フェールベルグの8次法

itable:

  * SDIRK*2*1_2: A-B安定な2次のSDIRK法
  * BILLINGTON*3*3_2: 安定性の低い3次の誤差予測子を持つ2次法
  * TRBDF2*3*3_2: 古典的なTR-BDF2法
  * KVAERNO*4*2_3: L安定な3次のESDIRK法
  * ARK324L2SA*DIRK*4*2*3: ケネディとカーペンターの3次法の暗黙的部分
  * CASH*5*2_4: キャッシュの4次L安定なSDIRK法
  * CASH*5*3_4: キャッシュの2次4次L安定なSDIRK法
  * SDIRK*5*3_4: ハイアーの4次SDIRK法
  * KVAERNO*5*3_4: クヴェルノの4次ESDIRK法
  * ARK436L2SA*DIRK*6*3*4: ケネディとカーペンターの4次法の暗黙的部分
  * KVAERNO*7*4_5: クヴェルノの5次ESDIRK法
  * ARK548L2SA*DIRK*8*4*5: ケネディとカーペンターの5次法の暗黙的部分

これらは、例えば次のように設定できます。

```julia
ARKODE(Sundials.Explicit(),etable = Sundials.DORMAND_PRINCE_7_4_5)
ARKODE(Sundials.Implicit(),itable = Sundials.KVAERNO_4_2_3)
```

### 方法の選択

  * method - これは暗黙的方程式を解くための方法です。BDFの場合、これはデフォルトで:Newtonに設定され、アダムスの場合は:Functionalに設定されます。これらの選択は、Sundials.jlマニュアルで推奨されるペアリングに一致します。ただし、:Newtonメソッドを使用すると、反復回数は少なくなりますが、:Function反復アプローチよりも多くのメモリを必要とすることに注意してください。
  * linear_solver - これは:Newtonメソッドで使用される線形ソルバーです。

### 線形ソルバーの選択

線形ソルバーの選択肢は次のとおりです。

  * :Dense - 密な線形ソルバー。
  * :Band - バンド行列のヤコビアンに特化したソルバー。使用する場合は、jac*upperおよびjac*lowerを介して上部および下部の非ゼロ対角線の位置を設定する必要があります。
  * :LapackDense - Juliaが提供するOpenBLASリンクのLAPACKを使用した密な線形ソルバーのバージョン。これは大規模なシステムでは:Denseよりも高速ですが、小規模なシステム（<100 ODE）では顕著なオーバーヘッドがあります。
  * :LapackBand - Juliaが提供するOpenBLASリンクのLAPACKを使用したバンド線形ソルバーのバージョン。これは大規模なシステムでは:Bandよりも高速ですが、小規模なシステム（<100 ODE）では顕著なオーバーヘッドがあります。
  * :Diagonal - この方法は対角ヤコビアンに特化しています。
  * :GMRES - GMRES法。推奨される最初の選択のクリロフ法。
  * :BCG - バイ共役勾配法。
  * :PCG - 前処理された共役勾配法。対称線形システム専用。
  * :TFQMR - TFQMR法。
  * :KLU - スパース因子分解法。ユーザーがヤコビアンを指定する必要があります。ヤコビアンはODEProblem型でスパース行列として設定する必要があります。

### 前処理器

ここで`prec`は前処理器関数`prec(z,r,p,t,y,fy,gamma,delta,lr)`であり、次のようになります。

  * `z`: 計算された出力ベクトル
  * `r`: 線形システムの右辺ベクトル
  * `p`: パラメータ
  * `t`: 現在の独立変数
  * `du`: 現在の`f(u,p,t)`の値
  * `gamma`: `W = M - gamma*J`の`gamma`
  * `delta`: 反復法の許容誤差
  * `lr`: `lr=1`（左）または`lr=2`（右）前処理のフラグ

`psetup`は、ヤコビアン情報を事前計算するための前処理器セットアップ関数`psetup(p, t, u, du, jok, jcurPtr, gamma)`です。ここで：

  * `p`: パラメータ
  * `t`: 現在の独立変数
  * `u`: 現在の状態
  * `du`: 現在の`f(u,p,t)`
  * `jok`: ヤコビアンを更新する必要があるかどうかを示すbool
  * `jcurPtr`: ヤコビアンが更新されたかどうかを示すIntへの参照。ヤコビアンが更新された場合は`jcurPtr[]=true`を設定し、更新されていない場合は`jcurPtr[]=false`を設定します。
  * `gamma`: `W = M - gamma*J`の`gamma`

`psetup`は`prec`が設定されている場合はオプションです。

### 追加オプション

追加のオプションの詳細については、[ARKODEマニュアル](https://computing.llnl.gov/sites/default/files/ark_guide-4.7.0.pdf)を参照してください。
