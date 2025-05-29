DiscreteDP型は、離散動的プログラミングモデルのパラメータを指定するためのものです。状態-行動ペアの定式化

##### パラメータ

  * `R::Array{T,NR}` : 報酬配列
  * `Q::Array{T,NQ}` : 遷移確率配列
  * `beta::Float64`  : 割引因子
  * `s_indices::Vector{Tind}`: 状態インデックス。SA定式化を使用しない限り空です
  * `a_indices::Vector{Tind}`: 行動インデックス。SA定式化を使用しない限り空です
  * `a_indptr::Vector{Tind}`: 行動インデックスポインタ。SA定式化を使用しない限り空です

##### 戻り値

  * `ddp::DiscreteDP` : DiscreteDPオブジェクトのコンストラクタ
