DiscreteDP型は、離散動的プログラミングモデルのパラメータを指定するためのものです。密行列の定式化

##### パラメータ

  * `R::Array{T,NR}` : 報酬配列
  * `Q::Array{T,NQ}` : 遷移確率配列
  * `beta::Float64`  : 割引因子

##### 戻り値

  * `ddp::DiscreteDP` : DiscreteDPオブジェクトのコンストラクタ
