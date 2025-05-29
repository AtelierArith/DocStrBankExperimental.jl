`fuv_grating1_flux_calib(lamA, netsrc_spec_counts_per_s_A[,order=-2])`

FUV-Grating1からの波長キャリブレーション済みカウントスペクトルをフラックスキャリブレーションします。

この関数は、カウントスペクトルの各波長における有効面積を計算し、その後、有効面積を使用してネットカウントレートをCGS単位のf_λに変換します。

...

# 引数

## 必須

-`lamA::Array{Float64}`: Å単位の波長の配列。 -`netsrc_spec_counts_per_s_A::Array{Float64}`: 波長配列に対応する背景補正済みカウント/s/Åの配列。

## オプション

-`Order::Number`: グレーティングオーダー -2（デフォルト）または -1。

...
