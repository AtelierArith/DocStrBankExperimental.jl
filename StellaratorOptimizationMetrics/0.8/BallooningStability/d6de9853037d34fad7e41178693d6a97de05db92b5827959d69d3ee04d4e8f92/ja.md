```
cobra(eq, surfs, nwells, θs, ζs, mode=1, geom_input=true, tokamak_input=false, lscreen=true)
```

CobraVmecコードに基づいてバルーニング平衡を計算します。元々はSanket PatilによってFortranからJuliaに変換され、Aaron Baderによって書き直されました。

# 引数

  * `eq::E`: VmecまたはDESC（最終的には）平衡
  * `slist::Vector{Int64}`: s値のリスト
  * `nwells::Int64`: 含めるヘリカルウェルの数

# オプション入力

  * `θs::Vector{Float64}`: 開始θ値のベクトル（ラジアン単位）
  * `ζs::Vector{Float64}`: 開始ζ値のベクトル（フィールド周期に正規化されたラジアン単位）
  * `mode::Int64`: モード番号、1は最も不安定なモード
  * `geom_input::Bool`: フラグ、デフォルトはtrue
  * `tokamak_input::Bool`: フラグ、デフォルトはfalse、これを使用するかどうかは不明
  * `lscreen::Bool`: フラグ、画面への出力、デフォルトはtrue
