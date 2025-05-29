データを要求されたサイズとタイプのウィンドウを使って畳み込みで平滑化します。

##### 引数

  * `x::Array`: 平滑化するデータを含む配列
  * `window_len::Int(7)`: ウィンドウの長さを与える奇数の整数
  * `window::AbstractString("hanning")`: ウィンドウタイプを与える文字列。可能な値は `flat`, `hanning`, `hamming`, `bartlett`, または `blackman` です。

##### 戻り値

  * `out::Array`: 平滑化されたデータの配列
