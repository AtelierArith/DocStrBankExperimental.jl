```
running_median(input, window_length, tapering=:symmetric; kwargs...) -> output
```

入力配列に対して `window_length` の中央値フィルタを実行し、結果を返します。

入力配列が多次元の場合、中央値は最初の次元、すなわちすべての列に対して独立して実行されます。

## テーパリング

テーパリングは、入力の端での動作を決定します。利用可能なテーパリングは次のとおりです。

  * `:symmteric` または `:sym`: 出力配列の各点の周りでウィンドウが対称になるように、常にウィンドウを2ずつ増やしたり減らしたりします。`window_length` が奇数の場合、出力は入力と同じ長さになります。`window_length` が偶数の場合、出力は1つ要素が少なくなります。
  * `:asymmetric` または `:asym`: 次の出力値を計算する際に、常に1つの要素を追加または削除します。配列の端で非対称のウィンドウを作成します。入力がNの長さの場合、出力はN+window_length-1の要素の長さになります。
  * `:asymmetric_truncated` または `:asym_trunc`: 非対称と同じですが、長さを `:symmetric` に合わせるために始まりと終わりで切り捨てられます。
  * `:none` または `:no`: 端に向かってテーパリングは行いません。入力にNの要素がある場合、出力はN-window_length+1の長さのみになります。これは、[RollingFunctions](https://github.com/JeffreySarnoff/RollingFunctions.jl) の "roll" に相当します。
  * `:beginning_only` または `:start`: 始まりでは常にウィンドウを1つ増やしますが、終わりはテーパリングしません。これは非対称に相当しますが、出力の長さが入力の長さに一致するように終わりで切り捨てられます。これは、[RollingFunctions](https://github.com/JeffreySarnoff/RollingFunctions.jl) の "run" に相当します。

偶数の `window_length` を選択した場合、出力配列の要素は連続した基盤軸上の入力要素の間に位置します。

`:beginning_only` を除いて、すべてのテーパリングは入力配列の中央に関して鏡対称です。

## キーワード引数

  * `nan=:include`: デフォルトでは、ウィンドウ内のNaN値は中央値をNaNにします。`nan = :ignore` を使用してNaN値を無視し、ウィンドウ内の残りの値に対して中央値を計算します。ウィンドウ内にNaNのみがある場合、中央値は常にNaNになります。
  * `output_eltype=Float64`: 出力配列の要素型。出力要素型はFloat64および入力要素型からの変換を許可する必要があります。例外は、テーパリングが `:no` または `:sym` の奇数ウィンドウ長の場合で、この場合、出力要素型は入力要素型からの変換のみを許可すればよいです。

## パフォーマンス

基盤となるアルゴリズムは、入力の長さNとウィンドウ長wに対してO(N log w)としてスケールする必要があります。
