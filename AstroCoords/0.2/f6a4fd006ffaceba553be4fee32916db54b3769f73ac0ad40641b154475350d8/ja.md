```
USM7{T} <: AstroCoord
```

統一状態モデル軌道要素。速度ホドグラフとクォータニオンを使用した軌道の7次元パラメータ化 C - 放射ベクトルに対して軌道面に横たわる速度ホドグラフ成分 Rf1 - 離心ベクトルの90度前方にある速度ホドグラフ成分 - 中間回転フレームのX軸に沿った Rf2 - 離心ベクトルの90度前方にある速度ホドグラフ成分 - 中間回転フレームのY軸に沿った ϵO1 - 第1虚数クォータニオン成分 ϵO2 - 第2虚数クォータニオン成分 ϵO3 - 第3虚数クォータニオン成分 η0 - 実数クォータニオン成分

コンストラクタ USM7(C, Rf1, Rf2, ϵO1, ϵO2, ϵO3, η0) USM7(X::AbstractArray) USM7(X::AstroCoord, μ::Number)
