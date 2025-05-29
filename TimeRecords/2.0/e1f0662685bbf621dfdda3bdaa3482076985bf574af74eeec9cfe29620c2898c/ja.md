TimeSeriesCollector{T}(interval::Second, delay::Second, timer::RefValue{DateTime}, data::Dict{String, TimeSeries{T}})

主に順序通りに到着するタグ付き時間記録 Pair{String=>TimeRecord{T}} を収集するために使用され、'interval' で取得されるように設計されています。

  * 'interval' は収集間隔（またはデータがアルゴリズムに供給されるウィンドウサイズ）です。ゼロに設定すると、間隔はタイムスタンプ間の距離になります。
  * 'delay' はデータを収集するために間隔を超えて待つ時間の量です。これにより、わずかに順序が異なるデータに対してアルゴリズムが堅牢になります。
  * 'timer' は次の収集間隔の開始を示す DateTime リファレンスです。
  * 'data' は収集したデータを保存する TimeSeries の Dict です。
