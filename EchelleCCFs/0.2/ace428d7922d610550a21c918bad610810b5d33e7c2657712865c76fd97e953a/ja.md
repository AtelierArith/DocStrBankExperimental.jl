`calc_ccf_chunk( chunk, ccf_plan )` スペクトルの1チャンクのCCFを計算するための便利な関数。

# 入力:

  * `ccf_out`:  出力を格納するための `AbstractArray`
  * `chunk`: CCFを計算するためのChunkOfSpectrum
  * `ccf_plan`: 現在のところ、CCF計算のためのline*list、mask*shape、およびその他のパラメータを提供するBasicCCFPlan

# オプション引数:

  * `assume_sorted`:  trueの場合、line_listが波長でソートされているかのチェックをスキップ
  * `calc_ccf_var`:  trueの場合、ccfの各値の分散の推定も計算

# 戻り値:

  * ccfプランからのmask_shapeとline listを使用して評価されたスペクトルの1チャンクのCCF
