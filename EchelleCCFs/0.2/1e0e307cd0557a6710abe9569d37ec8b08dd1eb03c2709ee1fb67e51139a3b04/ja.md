`calc_ccf_chunklist_timeseries( chunklist_timeseries, line_list )` スペクトルのタイムシリーズのCCFを計算するための便利な関数で、各スペクトルにはチャンクリストがあります。利用可能な場合は複数のスレッドを使用します。

# 入力:

  * chunklist_timeseries

# オプション引数:

  * ccf_plan (BasicCCFPlan())
  * verbose (false)

# 戻り値:

スペクトルのチャンクリスト内のすべてのチャンクにわたって合計されたCCFで、ccf*planを使用して評価されます。提供されたccf*planは、チャンクリスト*タイムシリーズ内のすべてのスペクトルに対して、その順序で確実に出現するラインのみを含むカスタムccf*planを作成するためのテンプレートとして使用されることに注意してください。
