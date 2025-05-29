```
MRSForward(R::Real, zgrid::AbstractVector{<:Real},
qgrid::AbstractVector{<:Real}, ϕ::Real, Be::Real,
condLEM::ConductivityModel; nrvals = 200, temp=300.0,
qwe=true)
```

円形ループのために計算されたカーネルを持つ `MRSForward` 前方モデリングオブジェクトを返します。

パラメータ：

  * `R`: メートル単位のループ半径
  * `zgrid`: 地表下のメートル単位の深さセル境界
  * `qgrid`: 実験に使用されるパルスモーメント（アンペア秒単位）
  * `ϕ`: ラジアン単位の磁場傾斜
  * `Be`: テスラ単位の地球磁場の大きさ
  * `condLEM`: `ConductivityModel` オブジェクトとしての層状地球導電率モデル

オプションのパラメータ：

  * `nrvals`: カーネルの水平積分を評価するために使用する放射点の数
  * `temp`: ケルビン単位の温度、平衡磁化の大きさに影響を与えます
  * `qwe`: カーネルのハンケルトランスフォームを評価するために外挿を伴う数値積分（QWE）を使用するかどうか

これは遅くなりますが、代替の801点デジタルフィルターよりも浅い深さでより正確です。
