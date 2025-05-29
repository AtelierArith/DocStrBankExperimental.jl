空間に作用するベクトルのような u のための変換演算子を設定します

args:     - space::AbstractSpace     - u::AbstractVecOrMat 入力プロトタイプのサイズ (N,) または (N,K)       ここで N は length(space) です。 K はバッチサイズです。

ret:     - space::AbstractSpace `u` に作用できる変換演算子を持つ
