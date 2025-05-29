水平拡散のためのスペクトルフィルター。フィールドは次のとおりです：

  * `trunc::Int64`: スペクトル解像度
  * `nlayers::Int64`: 垂直レベルの数
  * `shift::Any`: [OPTION] 拡散を高い（正のシフト）または低い（負のシフト）波数にシフトし、truncに対して相対的
  * `scale::Any`: [OPTION] スケール選択性、シグモイドの急峻さ、値が高いほど選択的
  * `time_scale::Dates.Second`: [OPTION] 拡散の時間スケール
  * `time_scale_div::Dates.Second`: [OPTION] 発散のための強い拡散時間スケール
  * `resolution_scaling::Any`: [OPTION] truncで時間スケールを短縮するための解像度スケーリング
  * `power::Any`: [OPTION] tanh関数の累乗
  * `power_div::Any`: [OPTION] 発散のためのtanh関数の累乗
  * `expl::Any`
  * `impl::Any`
  * `expl_div::Any`
  * `impl_div::Any`
