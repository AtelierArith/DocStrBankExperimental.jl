ヒストグラムアキュムレーターを構築します。

引数:

  * `min` - 最小値 [`T(0)`]
  * `width` - ビンサイズ [`T(1)`]
  * `max` - 最大値。`min`以下に設定すると、ヒストグラムが自動的にサイズを調整します。 [`min`]
  * `count_below_min` - `min`未満の値を無視するか、最初のビンにカウントするか [`false`]
  * `count_above_max` - `max`を超える値を無視するか、最後のビンにカウントするか [`false`]
