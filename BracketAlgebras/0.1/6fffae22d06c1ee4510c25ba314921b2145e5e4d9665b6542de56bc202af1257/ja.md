```
BracketAlgebra{T<:RingElement} <: AbstractBracketAlgebra{T}
```

型 `T` の係数を持つブラケット代数。

# フィールド

  * `d::Int`: 基本射影空間 P^`d` の次元
  * `n::Int`: 考慮される点の数
  * `R::MPolyRing{T}`: ブラケット代数の要素を表す AbstractAlgebra 多変数多項式環（内部使用のため）
  * `point_ordering::Vector{Int}`: テーブル順序を誘導する `n` 点インデックスの順序。`point_ordering[1] < point_ordering[2] < ... < point_ordering[n]`。
  * `variables::Bijection{Vector{Int},<:MPolyRingElem{T}}`: ブラケットから多項式環 `R` の対応する単項式への全単射
  * `point_labels::Vector`: 各点の点ラベル
