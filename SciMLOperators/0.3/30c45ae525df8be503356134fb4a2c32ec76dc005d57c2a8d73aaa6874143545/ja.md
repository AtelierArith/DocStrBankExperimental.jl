行列フリー演算子は関数によって与えられます

  * `op`:  シグネチャ op(u, p, t) を持つ関数（もし isinplace の場合は op(v, u, p, t)）
  * `op_adjoint`:  隣接演算子
  * `op_inverse`:  逆演算子
  * `op_adjoint_inverse`:  隣接逆演算子
  * `traits`:  特性
  * `p`:  パラメータ
  * `t`:  時間
  * `cache`:  キャッシュ
