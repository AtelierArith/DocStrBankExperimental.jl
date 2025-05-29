mp2rage*T1maps(im*MP2::Array{T},p::ParamsMP2RAGE;T1Range=1:10000,effInv = 0.96) where T <: Real

MP2RAGEパラメータからルックアップテーブルを計算します。キーワード radial = false は、信号を計算するために中央エコーのみが使用されることを意味します（Cartesian取得の標準的な方法）。radial = true の場合、すべてのエコーが合計されます。

# 引数

  * `im_MP2::Array{T}`
  * `p::ParamsMP2RAGE`

# キーワード

  * T1Range = 1:10000
  * effInv = 0.96
  * radial = false

# 戻り値

  * T1map
  * T1Range
  * lookUpTable

# 参考文献

  * Marques JP, Kober T, Krueger G, van der Zwaag W, Van de Moortele P-F, Gruetter R. MP2RAGE, a self bias-field corrected sequence for improved segmentation and T1-mapping at high field. NeuroImage 2010;49:1271–1281 doi: 10.1016/j.neuroimage.2009.10.002.
