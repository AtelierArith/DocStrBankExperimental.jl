totaldev(data, rate; [frequency=false], [overlapping=true], [taus=Octave]) 総偏差を計算します

#パラメータ:

  * `<data>`:			位相または周波数として偏差を計算するデータ配列。
  * `<rate>`:			与えられたデータのレート。
  * `[frequency]`:		`data`が周波数データを含む場合は真、それ以外の場合（デフォルト）は位相データと見なされます。
  * `[overlapping]`:	重複偏差を計算する場合は真（デフォルト）、そうでない場合は偽。
  * `[taus]`:			偏差を計算するためのタウ。これは、AllanTauDescriptor型 `AllTaus, Decadade, HalfDecade, Octave, HalfOctave, QuarterOctave`、計算するためのタウの配列、カスタム対数スケールを構築するための浮動小数点数、または特定の数の対数間隔のポイントを構築するための整数のいずれかです。

#戻り値: 名前付きタプル (tau, deviation, error, count)

  * `tau`:		使用されたタウ。
  * `deviation`:	計算された偏差。
  * `error`:		それぞれの誤差。
  * `count`:		各偏差に寄与する項の数。
