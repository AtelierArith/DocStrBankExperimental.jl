`calc_ccf_and_var_chunk!( chunk, ccf_plan )` 各 "CCF ピクセル" の CCF と分散を計算するための便利な関数で、`ccf*plan` からの mask*shape とラインリストを使用して評価されます。

# 入力:

  * `ccf_out`:  出力を格納するための `AbstractArray`
  * `ccf_var_out`:  出力を格納するための `AbstractArray`
  * `chunk`: CCF を計算するための ChunkOfSpectrum
  * `ccf_plan`: 現在のところ、CCF を計算するためのラインリスト、mask*shape、およびその他のパラメータを提供する BasicCCFPlan です。

# オプション引数:

  * `var`: 各ピクセルに使用する分散を持つ `AbstractArray` (chunk の値を上書きします)
  * `assume_sorted`: true の場合、line_list が波長でソートされているかどうかのチェックをスキップします。

# 名前付きタプルを返します:

  * `ccf_out`:
  * `ccf_var_out`:
