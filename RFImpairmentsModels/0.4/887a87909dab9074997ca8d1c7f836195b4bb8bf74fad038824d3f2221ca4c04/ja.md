入力信号 `x` に非線形PAモデルで定義された構造 `pa` に従ってパワーアンプの非線形性を適用します。バージョンは3つあります。

  * 出力 `y` を割り当てるもの addNonLinearPA(x,pa)
  * 最初の入力をインプレースで変更するもの addNonLinearPA!(y,x,pa)
  * 入力信号をインプレースで変更するもの addNonLinearPA!(x,pa)
