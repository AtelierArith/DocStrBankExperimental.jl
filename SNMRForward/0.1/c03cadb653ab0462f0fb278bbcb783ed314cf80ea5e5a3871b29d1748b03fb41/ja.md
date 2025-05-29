```
MRSForward_square(L::Real, zgrid::AbstractVector{<:Real},
qgrid::AbstractVector{<:Real}, ϕ::Real, θ::Real, Be::Real,
condLEM::ConductivityModel; nxpoints = 128, temp=300.0)
```

`MRSForward` 前方モデリングオブジェクトを返し、正方形ループのために計算されたカーネルを持ちます。

パラメータ:

  * `L`: メートル単位のループ半径
  * `zgrid`: 地表下のメートル単位の深さセル境界。
  * `qgrid`: 実験に使用されるパルスモーメント、アンペア秒単位。
  * `ϕ`: ラジアン単位の磁場傾斜。
  * `θ`: ループの向きと磁北との間の水平角度、ラジアン単位。
  * `Be`: テスラ単位の地球磁場の大きさ。
  * `condLEM`: `ConductivityModel` オブジェクトとしての層状地球導電率モデル。

オプションのパラメータ:

  * `nxpoints`: カーネルの水平統合のために各次元で使用するポイントの数。
  * `temp`: ケルビン単位の温度、平衡磁化の大きさに影響します。
