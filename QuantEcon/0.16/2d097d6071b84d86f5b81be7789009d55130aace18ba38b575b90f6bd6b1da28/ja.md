ベルマン演算子は、与えられた価値関数 $v$ に対して更新された価値関数 $Tv$ を計算して返します。

この関数は、入力 `v` を `Tv` で埋め、入力 `sigma` を対応するポリシールールで埋めます。

##### パラメータ

  * `ddp::DiscreteDP`: ddp モデル
  * `v::AbstractVector{T<:AbstractFloat}`: 現在の価値関数の推定値。この配列は上書きされます
  * `sigma::AbstractVector`: ポリシー関数を保持するためのバッファ配列。初期値は使用されず、上書きされます

##### 戻り値

  * `Tv::Vector`: 更新された価値関数ベクトル
  * `sigma::typeof(sigma)`: ポリシールール
