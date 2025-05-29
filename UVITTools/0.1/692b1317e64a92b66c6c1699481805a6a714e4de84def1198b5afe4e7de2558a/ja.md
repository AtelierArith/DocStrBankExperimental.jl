`nuv_grating_m1_flux_calib(lamA, netsrc_spec_counts_per_s_A)`

NUV-Grating1のオーダー=-1からの波長キャリブレーションされたカウントスペクトルをフラックスキャリブレーションします。

この関数は、カウントスペクトルの各波長における有効面積を計算し、その後、有効面積を使用してネットカウントレートをCGS単位のf_λに変換します。

...

# 引数

## 必須

  * `lamA::Array{Float64}`: Å単位の波長の配列。 - `netsrc_spec_counts_per_s_A::Array{Float64}`: 波長配列に対応する背景補正されたカウント/s/Åの配列。

## オプション

  * なし。

...
