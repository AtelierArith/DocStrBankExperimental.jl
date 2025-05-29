NautyResultsは以下のインターフェースを満たさなければなりません

  * strhsh: 同型類を表す文字列値
  * orbits: Cset部分の軌道への分割、例えばE#2 = E#5の場合、これらの2つの要素は対称です
  * generators: 自動同型群の生成自動同型
  * ngroup: 自動同型群の要素数
  * canonmap: 入力から標準同型への同型
  * canon: 標準同型（`canonmap`の共変）
