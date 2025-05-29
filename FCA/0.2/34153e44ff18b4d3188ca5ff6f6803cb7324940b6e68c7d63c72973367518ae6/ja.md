grad*neg*abs*sum*kurt(W, Z)

この関数は、neg*abs*sum_kurt(W'*Z) の W に関する勾配を計算します。

# 引数

  * `W`: size(W, 1) = size(Z, 1) となる行列
  * `Z`: 同じ長さのベクトルの配列で、混合独立信号の実現として扱われます

# 出力

  * `grad`: neg*abs*sum_kurt(W'*Z) の W に関する勾配
