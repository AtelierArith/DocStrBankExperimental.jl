```
plot_SolSum(sol::Sol{T,O},xvars::Int...;interp=0.0001,note=" "::String,xlims=(0.0,0.0)::Tuple{Float64, Float64},ylims=(0.0,0.0)::Tuple{Float64, Float64},legend=:true::Bool) where{T,O}
```

変数 xvars の合計のプロット。

# 引数

  * `sol::Sol{T,O}`: 解構造体。
  * `xvars::Int...`: 合計する変数のインデックス。インデックスが提供されない場合、すべての変数が合計されます。
  * `interp::Float64`: 補間ステップ。
  * `note::String`: プロットのタイトルに追加するノート。
  * `xlims::Tuple{Float64, Float64}`: プロットの x 軸の制限。
  * `ylims::Tuple{Float64, Float64}`: プロットの y 軸の制限。
  * `legend::Bool`: 凡例を表示するかどうかを示すブール値。
