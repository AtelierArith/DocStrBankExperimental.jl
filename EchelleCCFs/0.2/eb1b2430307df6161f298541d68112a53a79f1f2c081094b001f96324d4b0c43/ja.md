`calc_ccf_chunklist ( chunklist, ccf_plans )` スペクトルのチャンクリストに基づいてCCFを計算するための便利な関数です。

# 入力:

  * chunklist
  * 各チャンクに対するccfプランのベクトル

# オプション引数:

  * `assume_sorted`:  trueの場合、line_listが波長でソートされているかのチェックをスキップします

# 返り値:

スペクトルのチャンクリスト内のすべてのチャンクにわたって合計されたCCFで、各チャンクのccfプランからのline listとmask_shapeを使用して評価されます。
