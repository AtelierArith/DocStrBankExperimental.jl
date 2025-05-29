ローカル大気密度をNRLMSISE00大気モデルを使用して計算します。

引数:

  * `epc::Epoch`: 計算のエポック。宇宙天気データを検索するために使用されます
  * `x::AbstractArray{<:Real, 1}`: 測地座標での衛星状態 [経度, 緯度, 高度]
  * `use_degrees:Bool`: `true` の場合、測地入力を度単位として解釈します

戻り値:

  * `rho:Float64`: ローカル大気密度 [kg/m^3]

注意:

1. NRLMSISE00のgtd7dサブルーチンを使用してローカル大気密度を計算します。このサブルーチンは、500 kmの高度以上の衛星にとって重要なローカル密度における異常酸素の寄与を含んでいます。

参考文献:

1. *Picone, JM, et al.* NRLMSISE-00経験的モデルの大気: 統計的比較と科学的問題 *Journal of Geophysical Research: Space Physics*
