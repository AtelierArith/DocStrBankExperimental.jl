```
sensitivity(omc::OMCSession, Vp, Vv, Ve=[1e-2])
```

OpenModelicaオブジェクトの数値感度を計算するためのメソッド。

## 引数

  * `omc::OMCSession`:                OpenModelicaコンパイラセッション。
  * `Vp::Array{<:AbstractString, 1}`:   Modelicaパラメータ名。
  * `Vv::Array{<:AbstractString, 1}`:   Modelica変数名。
  * `Ve::Array{Float64, 1}`:          パラメータの励起; デフォルトはスカラー1e-2

## 戻り値

  * `VSname::Vector{Vector{String}}`:             感度名のベクトル
  * `VSarray::Vector{Vector{Vector{Float64}}}`:   感度のベクトル: パラメータごとの要素のベクトル

各要素は変数ごとの時系列を含む
