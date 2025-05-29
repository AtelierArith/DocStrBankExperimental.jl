```julia
mutable struct Params
```

半導体デバイスのドリフト-拡散シミュレーションの物理領域依存パラメータを保持する構造体です。

  * `numberOfNodes::Int64`: ドメイン $\mathbf{\Omega}$ の離散化に使用されるノードの数。
  * `numberOfRegions::Int64`: ドメイン $\mathbf{\Omega}$ 内のサブリージョン $\mathbf{\Omega}_k$ の数。
  * `numberOfBoundaryRegions::Int64`: 境界領域 $(\partial \mathbf{\Omega})_k$ の数で、$\partial \mathbf{\Omega} = \cup_k (\partial \mathbf{\Omega})_k$ となります。ここでは内境界と外境界が計算されます。
  * `numberOfCarriers::Int64`: 移動する電荷キャリアの数。
  * `invertedIllumination::Int64`: 照明の方向に関するパラメータ。照明が左から来る場合はこの値を1に設定します。そうでない場合、照明が右から来る場合はこの値を-1に設定します。
  * `temperature::Float64`: 与えられた定数温度。
  * `UT::Float64`: 熱電圧で、$U_T = k_B T / q$ と読み取ります。
  * `γ::Float64`: ブレイクモア統計のパラメータ（一般化SGフラックスに必要）。
  * `r0::Float64`: 内部境界条件の電気化学反応の前因子。
  * `prefactor_SRH::Float64`: 定常SRH再結合の前因子。
  * `generationPeak::Float64`: ビール-ランバート生成プロファイルの生成ピークのシフトに関するパラメータ。
  * `SchottkyBarrier::Vector{Float64}`: 現在のショットキー接触における与えられたショットキー障壁の配列。
  * `contactVoltage::Vector{Float64}`: 適用された電圧の定数値を含む配列。
  * `bψEQ::Vector{Float64}`: ディリクレ境界条件の場合の電位の定数値を含む配列。
  * `chargeNumbers::Vector{Float64}`: すべてのキャリア $\alpha$ に対する対応する電荷数 $z_\alpha$ を持つ配列。
  * `bBandEdgeEnergy::Matrix{Float64}`: 各キャリア $\alpha$ に対する各領域の対応する境界バンドエッジエネルギー値 $E_\alpha$ を持つ配列。
  * `bDensityOfStates::Matrix{Float64}`: 各キャリア $\alpha$ に対する対応する境界有効状態密度値 $N_\alpha$ を持つ配列。
  * `bMobility::Matrix{Float64}`: 各キャリア $\alpha$ に対する各境界領域の対応する境界移動度値 $\mu_\alpha$ を持つ2D配列。
  * `bDoping::Matrix{Float64}`: 各キャリア $\alpha$ に対する各領域の対応する境界ドーピング値を持つ2D配列。
  * `bVelocity::Matrix{Float64}`: ショットキー接触を仮定した場合の各キャリア $\alpha$ に対する各境界の対応する境界速度値を持つ2D配列。
  * `bReactionCoefficient::Matrix{Float64}`: 内部境界での反応係数を定義するための配列。
  * `recombinationSRHvelocity::Matrix{Float64}`: 電子とホールのための対応する再結合表面境界速度値を持つ2D配列。
  * `bRecombinationSRHTrapDensity::Matrix{Float64}`: 電子とホールのための対応する再結合表面境界密度値を持つ2D配列。
  * `bRecombinationSRHLifetime::Matrix{Float64}`: 対応する再結合表面再結合速度を持つ2D配列。
  * `bDensityEQ::Matrix{Float64}`: 境界での電荷キャリアの平衡密度を含む2D配列。
  * `doping::Matrix{Float64}`: 各領域の各キャリア $\alpha$ に対する対応するドーピング値を持つ2D配列。
  * `densityOfStates::Matrix{Float64}`: 各領域の各キャリア $\alpha$ に対する対応する有効状態密度値 $N_\alpha$ を持つ2D配列。
  * `bandEdgeEnergy::Matrix{Float64}`: 各領域の各キャリア $\alpha$ に対する対応するバンドエッジエネルギー値 $E_\alpha$ を持つ2D配列。
  * `mobility::Matrix{Float64}`: 各領域の各キャリア $\alpha$ に対する対応する移動度値 $\mu_\alpha$ を持つ2D配列。
  * `recombinationSRHLifetime::Matrix{Float64}`: 電子とホールのための対応するSRH寿命 $\tau_n, \tau_p$ を持つ2D配列。
  * `recombinationSRHTrapDensity::Matrix{Float64}`: 電子とホールのための対応する時間不変SRHトラップ密度 $n_{\tau}, p_{\tau}$ を持つ2D配列。
  * `recombinationAuger::Matrix{Float64}`: 電子とホールのための対応するオージェ係数を持つ2D配列。
  * `dielectricConstant::Vector{Float64}`: 領域依存の誘電率。
  * `dielectricConstantImageForce::Vector{Float64}`: 領域依存の画像力誘電率。
  * `generationIncidentPhotonFlux::Vector{Float64}`: 入射光子フラックスである生成プロセスの前因子に対する領域依存の配列。
  * `generationUniform::Vector{Float64}`: 一様生成率に対する領域依存の配列。
  * `generationAbsorption::Vector{Float64}`: 生成プロセスにおける吸収係数に対する領域依存の配列。
  * `recombinationRadiative::Vector{Float64}`: 放射再結合率に対する領域依存の配列。
