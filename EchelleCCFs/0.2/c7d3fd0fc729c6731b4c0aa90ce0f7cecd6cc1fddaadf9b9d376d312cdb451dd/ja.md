`calc_ccf_chunk!( ccf_out, chunk, ccf_plan )` スペクトルの1チャンクのCCFを計算するための便利な関数で、ccfプランからのmask_shapeとラインリストを使用して評価されます。

# 入力:

  * `ccf_out`: 出力を格納するための `AbstractArray`
  * `chunk`: CCFを計算するためのChunkOfSpectrum
  * `ccf_plan`: 現在のところ、ラインリスト、マスクシェイプ、およびCCF計算のための他のパラメータを提供するBasicCCFPlanのみ

# オプション引数:

  * `assume_sorted`: trueの場合、ラインリストが波長でソートされているかのチェックをスキップします

# 戻り値:

  * `ccf_out`
