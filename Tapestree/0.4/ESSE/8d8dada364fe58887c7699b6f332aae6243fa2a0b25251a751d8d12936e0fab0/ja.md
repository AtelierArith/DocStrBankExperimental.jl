```
simulate_sse(λ          ::Array{Float64,1},
             μ          ::Array{Float64,1},
             l          ::Array{Float64,1},
             g          ::Array{Float64,1},
             q          ::Array{Float64,1},
             β          ::Array{Float64,1},
             t          ::Float64,
             x          ::Array{Float64,1},
             y          ::Array{Float64,N},
             cov_mod    ::Tuple{Vararg{String}};
             δt         ::Float64 = 1e-4,
             ast        ::Int64   = 0,
             nspp_max   ::Int64   = 100_000,
             retry_ext  ::Bool    = true,
             rejectel0  ::Bool    = true,
             verbose    ::Bool    = true,
             rm_ext     ::Bool    = true,
             states_only::Bool    = false,
             start      ::Symbol  = :crown) where {N}
```

地理的**sse**モデルに従って木をシミュレートします。エリアの数と隠れた状態はパラメータベクトルから推測されますが、それらは互いにおよび共変量と一貫している必要があります。例についてはチュートリアルを参照してください。

# 引数

  * `λ::Array{Float64,1}`: エリア内およびエリア間の種分化のための率。
  * `μ::Array{Float64,1}`: グローバル絶滅につながるエリアごとの絶滅率。
  * `l::Array{Float64,1}`: ローカル絶滅につながるエリアごとの絶滅率。
  * `g::Array{Float64,1}`: エリア間のコロニゼーション率。
  * `q::Array{Float64,1}`: 隠れた状態間の遷移率。
  * `β::Array{Float64,1}`: 共変量のエリアごとの効果。
  * `t::Float64`: シミュレーション時間。
  * `x::Array{Float64,1}`: 共変量`y`がサンプリングされる時間。
  * `y::Array{Float64,N}`: 共変量の値、すなわち`f(x)`。多変量である可能性があります。
  * `cov_mod::Tuple{Vararg{String}}`: 共変量の影響を受ける率を指定します：`s`は種分化、`e`は絶滅、`g`はコロニゼーションを示します。1つ以上の指定が可能です。
  * `δt::Float64 = 1e-4`: シミュレーションを実行するための時間ステップ。小さいほど精度が高いですが、計算コストが高くなります。
  * `ast::Int64 = 0`: 初期状態。`0`は入力パラメータに基づくランダムサンプリングを指定します。
  * `nspp_max::Int64 = 100_000`: シミュレーションを停止するために許可される最大種数。
  * `retry_ext::Bool = true`: シミュレーションが絶滅した場合、自動的に再起動します。
  * `rejectel0::Bool = true`: 長さ0のエッジがあるシミュレーションを拒否します。
  * `verbose::Bool = true`: メッセージを表示します。
  * `rm_ext::Bool = true`: 出力から絶滅した分類群を削除します。
  * `states_only::Bool = false`: もしティップの状態のみを返す場合（高速）。
  * `start::Symbol  = :crown`: `crown`の場合、2つの系統を持つ種分化イベントの後に開始し、`stem`の場合は1つの系統から開始します。

# 戻り値

  * ティップ番号と対応する状態の辞書。
  * 親 -> 娘エッジの配列。
  * エッジの長さの配列。
  * 最大種数。
