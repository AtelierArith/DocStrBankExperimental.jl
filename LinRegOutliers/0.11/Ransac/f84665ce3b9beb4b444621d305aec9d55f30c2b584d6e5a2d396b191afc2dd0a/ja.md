```
ransac(setting; t, w=0.5, m=0, k=0, d=0, confidence=0.99)
```

与えられた回帰設定に対してRANSAC（1981）アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `t::Float64`: サンプルポイントが回帰ハイパープレーンにどれだけ近いかを示す閾値距離で、モデルに適合しているかどうかを判断します。
  * `w::Float64`: サンプルポイントがインライヤーである確率、デフォルトは0.5。
  * `m::Int`: 各イテレーションでモデルパラメータを推定するためにサンプリングするポイントの数。0に設定された場合、必要な最小数のpポイントを選択するデフォルトになります。
  * `k::Int`: 実行するイテレーションの数。0に設定された場合、外れ値確率とサンプルセットサイズに基づいて論文に記載された式に従って計算されます。
  * `d::Int`: モデルを受け入れるために必要な近接データポイントの数。デフォルトはデータポイントの数にインライヤー比を掛けたものです。
  * `confidence::Float64`: kが指定されていない場合に最適なイテレーション数を決定するために必要です。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列。

# 例

```julia-repl
julia> df = DataFrame(y=[0,1,2,3,3,4,10], x=[0,1,2,2,3,4,2])
julia> reg = createRegressionSetting(@formula(y ~ x), df)
julia> ransac(reg, t=0.8, w=0.85)
Dict{String,Array{Int64,1}} with 1 entry:
  "outliers" => [7]
```

# 参考文献

Martin A. Fischler & Robert C. Bolles (1981年6月). "Random Sample Consensus: A Paradigm for Model Fitting with Applications to Image Analysis and Automated Cartography" Comm. ACM. 24 (6): 381–395.
