```julia
mutable struct ElectrolyteData{Tγ, Tcache, Texp, Tlog, Tflux} <: LiquidElectrolytes.AbstractElectrolyteData
```

電解質のデータ。これは[`Base.@kwdef`](https://docs.julialang.org/en/v1/base/base/#Base.@kwdef)を使用して定義されており、キーワードコンストラクタを使用することができます。

```julia
    ElectrolyteData(nc=3,z=[-1,2,1])
```

この構造体には3つのフィールドグループがあります：

  * 問題パラメータ：これらはユーザーによって設定され、シミュレーションパラメータを提供するためのものです。
  * 派生値：これらはデフォルトで問題パラメータから導出されるか、いくつかの問題パラメータを設定した後に[`update_derived!`](@ref)を介して導出されます。
  * 固定値：これらは主に物理定数およびそれらから導出された値であり、変更されるべきではありません。
  * 予約フィールド：これらはシミュレーション中に情報を渡すために使用され、ユーザーによって設定されるべきではありません。

フィールド（予約フィールドは一部のアルゴリズムによって変更されます）：

  * `nc::Int64`: 帯電種の数 $N$。
  * `na::Int64`: 表面種の数
  * `iϕ::Int64`: 種リストにおける静電ポテンシャル $ϕ$ のインデックス。
  * `ip::Int64`: 種リストにおける圧力 `p` のインデックス
  * `D::Vector{Float64}`: 移動度係数 $D_i\; (i=1…N)$
  * `z::Vector{Int64}`: イオンの電荷数 $z_i\; (i=1…N)$
  * `M0::Float64`: 溶媒のモル質量 $M_0$
  * `M::Vector{Float64}`: イオンのモル質量 $M_i\; (i=1…N)$
  * `v0::Float64`: 溶媒のモル体積 $v_0$
  * `v::Vector{Float64}`: イオンのモル体積 $v_i\; (i=1…N)$
  * `κ::Vector{Float64}`: イオンの溶媒化数 $κ_i\; (i=1…N)$
  * `actcoeff!::Any`:     actcoeff!(γ, c, p, ::ElectrolyteData)

    活動係数関数。活動係数 $γ_i\; (i=1…N)$ をベクトル `γ` に書き込みます。デフォルト：[`DGML_gamma!`](@ref)。
  * `c_bulk::Vector{Float64}`: バルクイオン濃度 $c_i^b\; (i=1…N)$
  * `Γ_we::Int64`: 作業電極境界番号
  * `Γ_bulk::Int64`: バルク境界番号
  * `ϕ_bulk::Float64`: バルク電圧 $ϕ^b$
  * `p_bulk::Float64`: バルク圧力 $p^b$
  * `T::Float64`: 温度 $T$
  * `ε::Float64`: 溶媒の誘電率 $ε$
  * `rexp::Any`: 正則化指数関数、デフォルト：`exp`（非正則化）
  * `rlog::Any`: 正則化対数、デフォルト：`log`（非正則化）
  * `pscale::Float64`: 圧力スケーリング係数。デフォルト：1.0e9
  * `eneutral::Bool`: ローカル電気中性スイッチ。デフォルト：false
  * `upwindflux!::Any`: イオン種のためのアップウィンドフラックス計算方法。これにより、次の間で選択できます。

      * [`μex_flux!`](@ref)（デフォルト、強く推奨）：過剰化学ポテンシャル（SEDAN）スキーム
      * [`act_flux!`](@ref)：逆活動係数に基づくスキーム
      * [`cent_flux!`](@ref)：中央スキーム
  * `weights::Vector{Float64}`: ソルバー制御のための種の重み。
  * `solvepressure::Bool`: 圧力を解決します。

    これはデフォルトで `true` です。これを `false` に設定すると、2つの目的を果たすことができます：

      * 流れ方程式の解から圧力を使用する
      * 過剰化学ポテンシャルへの圧力寄与を無視する
  * `F::Float64`: ファラデー定数 $F$（固定）
  * `ε_0::Float64`: 真空の誘電率 $ε_0$（固定）
  * `RT::Float64`: 温度でスケーリングされたモル気体定数 $RT$（導出）
  * `Mrel::Vector{Float64}`: 溶媒化モル質量比 $m_i = \frac{M_i}{M_0} + κ_i \; (i=1… N)$（導出）
  * `vrel::Vector{Float64}`: 溶媒化モル体積比 $\hat v_i =  \frac{v_i}{v_0} + κ_i \; (i=1… N)$（導出）
  * `barv::Vector{Float64}`: 溶媒化モル体積 $\bar v_i = v_i + κ_i v_0 \; (i=1… N)$（導出）
  * `tildev::Vector{Float64}`: 圧力関連体積 $\tilde v_i = \bar v_i + m_i v_0 \; (i=1… N)$  （導出）
  * `γ_bulk::Vector{Float64}`: バルク界面での活動係数 $γ_i^b= γ_i(c_1^b … c_N^b, p^b) \; (i=1… N)$（導出）
  * `γk_cache::Any`: 活動係数計算のためのキャッシュ（予約）
  * `γl_cache::Any`: 活動係数計算のためのキャッシュ（予約）
  * `ϕ_we::Float64`: 作業電極電圧 $ϕ_{we}$（予約）スイープアルゴリズムによって境界データを渡すために使用されます。
  * `edgevelocity::Union{Float64, Vector{Float64}}`: エッジ速度の投影（予約）。
  * `scheme::Symbol`: スキームパラメータ。非推奨で無効。離散化スキームを変更するには、代わりに `upwindflux!` を使用してください。
