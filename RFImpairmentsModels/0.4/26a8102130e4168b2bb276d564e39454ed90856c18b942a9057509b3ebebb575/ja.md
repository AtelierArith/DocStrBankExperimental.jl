複素入力信号 x に対して、ゲインミスマッチ g (dB) と位相ミスマッチ ϕ にパラメータ化された IQ ミスマッチを適用します。このモデルは、ゲインを 2 つの等分されたゲインに分割し、位相を等分された位相に分割します。 [1] Matthias Hesse, Marko Mailand, Hans-Joachim Jentschel, Luc Deneire, Jerome Lebrun. Semi-Blind Cancellation of IQ-Imbalances. IEEE International Conference on Communications, May 2008, 北京, 中国. hal-00272886v1 関数には 3 つのバージョンがあります。

  * 出力 y を割り当てるもの y = addIQMismatch(x,g,ϕ) または y = addIQMismatch(g,s::IQMismatch)
  * 2 番目の入力を変更するもの addIQMismatch!(y,x,...)
  * インプレースで変更するもの: addIQMismatch!(x,...). 後者の場合、信号は IQ ミスマッチによって損なわれた信号で修正されます。
