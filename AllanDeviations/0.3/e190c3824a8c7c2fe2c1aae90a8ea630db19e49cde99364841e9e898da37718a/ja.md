hadamarddev(data, rate; [frequency=false], [overlapping=true], [taus=Octave]) ハダマード偏差を計算します

#パラメータ:

  * `<data>`:			偏差を計算するためのデータ配列。位相または周波数として。
  * `<rate>`:			与えられたデータのレート。
  * `[frequency]`:		`data`が周波数データを含む場合はtrue、そうでない場合（デフォルト）は位相データと見なされます。
  * `[overlapping]`:	重複偏差を計算する場合はtrue（デフォルト）、そうでない場合はfalse。
  * `[taus]`:			偏差を計算するためのタウ。これは、AllanTauDescriptor型の`AllTaus, Decadade, HalfDecade, Octave, HalfOctave, QuarterOctave`、計算するためのタウの配列、カスタム対数スケールを構築するための浮動小数点数、または特定の数の対数間隔のポイントを構築するための整数のいずれかです。

#戻り値: 名前付きタプル (tau, deviation, error, count)

  * `tau`:		使用されたタウ。
  * `deviation`:	計算された偏差。
  * `error`:		それぞれの誤差。
  * `count`:		各偏差に寄与する項の数。
