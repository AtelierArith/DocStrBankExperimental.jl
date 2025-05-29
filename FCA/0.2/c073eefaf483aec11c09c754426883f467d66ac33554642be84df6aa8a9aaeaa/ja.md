grad*ent*sum(W, Z)

この関数は、ent_sum(W'*Z) の W に関する勾配を計算します。

# 引数

  * `W`: size(W, 1) = size(Z, 1) である行列
  * `Z`: 同じ長さのベクトルの配列で、混合独立信号の実現として扱われます

# 出力

  * `grad`: ent_sum(W'*Z) の W に関する勾配
