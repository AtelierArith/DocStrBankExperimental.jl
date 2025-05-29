```
rumba_rec(dwi::MRI{T}, mask::MRI, odf_dirs::ODF=sphere_724, niter::Integer=600, λ_para::T=T(1.7*10^-3), λ_perp::T=T(0.2*10^-3), λ_csf::T=T(3.0*10^-3), λ_gm::T=T(0.8*10^-4), ncoils::Integer=1, coil_combine::String="SMF-SENSE", ipat_factor::Integer=1, use_tv::Bool=true) where T <: AbstractFloat
```

DWIsの堅牢で偏りのないモデルベースの球面逆変換（RUMBA-SD）再構成を行い、`RUMBASD`構造体を返します。

この方法を使用する場合は、次の文献を引用してください: Erick J. Canales-Rodríguez, et al. (2015). Spherical deconvolution of multichannel diffusion MRI data with non-Gaussian noise models and spatial regularization. PLoS ONE, 10(10), e0138910. https://doi.org/10.1371/journal.pone.0138910

# 引数

  * `dwi::MRI{T}`: 有効な `.bvec` および `.bval` フィールドを持つ `MRI` 構造体に格納された一連のDWI
  * `mask::MRI`: `MRI` 構造体に格納された脳マスクボリューム
  * `odf_dirs::ODF=sphere_724`: `ODF` 構造体に格納されたODFテッセレーションの頂点と面
  * `λ_para::T=T(1.7*10^-3)`: 単一のファイバーポピュレーションを持つ白質ボクセルにおける軸方向拡散率
  * `λ_perp::T=T(0.2*10^-3)`: 単一のファイバーポピュレーションを持つ白質ボクセルにおける放射方向拡散率
  * `λ_csf::T=T(3.0*10^-3)`: CSFボクセルにおける平均拡散率
  * `λ_gm::T=T(0.8*10^-4)`: 灰白質ボクセルにおける平均拡散率
  * `ncoils::Integer=1`: DWIsが並列イメージングで収集された場合の受信コイル要素の数、そうでない場合は1
  * `coil_combine::String="SMF-SENSE"`: 受信コイル要素からの信号を組み合わせるために使用された方法（可能な値: "SMF-SENSE" または "SoS-GRAPPA"; `ncoils` が1の場合は影響なし）
  * `ipat_factor::Integer=1`: DWIsが並列イメージングで収集された場合の加速因子、そうでない場合は1
  * `use_tv::Bool=true`: trueの場合、FOD再構成に全変動正則化項を含める

# 出力

`RUMBASD` 構造体内:

  * `.fodf`: 異方性コンパートメントの体積比（頂点ごとに1つ）
  * `.fgm`: GM等方性コンパートメントの体積比
  * `.fcsf`: CSF等方性コンパートメントの体積比
  * `.peak`: 5つのピークODF振幅の方向ベクトル
  * `.gfa`: 一般化された分数異方性
  * `.var`: 推定されたノイズ分散
  * `.snr_mean`: 推定された平均SNR
  * `.snr_std`: 推定されたSNR標準偏差

```
