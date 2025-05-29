```
lp([estimator], data, ynames; kwargs...)
```

指定された `estimator` を使用して、`data` テーブル内の列名 `ynames` の結果変数に対してローカルプロジェクションを推定します。`estimator` が指定されていない場合は、[`LeastSquaresLP`](@ref) が仮定されます。入力 `data` は `Tables.jl` 互換でなければなりません。

# キーワード

  * `xnames=()`: `data` からの同時回帰変数のインデックス。
  * `wnames=()`: `data` からの遅延制御変数のインデックス。
  * `nlag::Int=4`: 遅延制御変数に含める遅延の数。
  * `nhorz::Int=1`: 推定されるホライズンの総数。
  * `minhorz::Int=0`: 推定に関与する最小ホライズン。
  * `normalize::Union{VarIndexPair,Vector{VarIndexPair},Nothing}=nothing`: 対象の結果変数に対する初期の影響に基づいて、指定された回帰変数の大きさを正規化します。
  * `iv::Union{Pair,Nothing}=nothing`: 楽器とペアになった内生変数。
  * `firststagebyhorz::Bool=false`: 各ホライズンごとに第一段階回帰を別々に推定します。
  * `testweakiv::Bool=true`: 弱いIVのためのKleibergen-Paap rk統計量を計算します。
  * `states=nothing`: 状態依存仕様のための状態を表す変数。
  * `panelid::Union{Symbol,Integer,Nothing}=nothing`: パネル内のユニットを識別する変数。
  * `fes=()`: 固定効果を識別する変数。
  * `addpanelidfe::Bool=true`: ユニットの固定効果に `panelid` を使用します。
  * `panelweight::Union{Symbol,Integer,Nothing}=nothing`: パネル内のユニット間の重み。
  * `vce::CovarianceEstimator=HRVCE()`: 分散共分散推定量。
  * `subset::Union{BitVector,Nothing}=nothing`: 推定に使用される `data` のサブセット。
  * `addylag::Bool=true`: 結果変数の遅延を含めます。
  * `nocons::Bool=false`: 定数項を追加しません。
  * `TF::Type=Float64`: 推定に使用される数値型。
