離散動的プログラミングモデルのパラメータを指定するためのDiscreteDP型

##### パラメータ

  * `R::Array{T,NR}` : 報酬配列
  * `Q::Array{T,NQ}` : 遷移確率配列
  * `beta::Float64`  : 割引因子
  * `a_indices::Vector{Tind}`: 行動インデックス。SA定式化を使用しない限り空
  * `a_indptr::Vector{Tind}`: 行動インデックスポインタ。SA定式化を使用しない限り空

##### 戻り値

  * `ddp::DiscreteDP` : DiscreteDPオブジェクト
