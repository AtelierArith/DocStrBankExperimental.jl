スコットランドのヒルレースデータ

# コンポーネント

  * `dist::AbstractVector{Float64}`: マイル単位の距離（独立変数）。
  * `climb::AbstractVector{Float64}`: フィート単位の高さ（独立変数）。
  * `time::AbstractVector{Float64}`: 時間単位の記録（従属変数）。

# モデル

time ~ dist + climb

# 参考文献

A.C. Atkinson (1986) コメント: 診断的回帰分析の側面。Statistical Science 1, 397-402。
