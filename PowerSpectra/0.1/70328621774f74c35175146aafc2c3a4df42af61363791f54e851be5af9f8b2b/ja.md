```
CovarianceWorkspace(m_i, m_j, m_p, m_q; lmax::Int=0)
```

共分散計算のための入力とキャッシュ。共分散行列は、4つのフィールドとスピンのマスクを関連付けます。この構造は、マスクとノイズ加重マスクの間のさまざまなクロススペクトルをキャッシュします。デフォルトでは、Float64精度で動作します。

# 引数:

  * `m_i::CovField{T}`: マップ i
  * `m_j::CovField{T}`: マップ j
  * `m_p::CovField{T}`: マップ p
  * `m_q::CovField{T}`: マップ q

# キーワード

  * `lmax::Int=0`: 共分散行列を計算するための最大多極子
