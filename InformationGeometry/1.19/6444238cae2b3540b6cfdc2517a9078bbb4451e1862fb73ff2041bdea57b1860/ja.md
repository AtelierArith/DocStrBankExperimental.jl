```
ConditionGrid(DMs::AbstractVector{<:AbstractDataModel}, Trafos::AbstractVector{<:Function}, mle::AbstractVector, LogPriorFn::Union{Nothing,Function}=nothing; Domain::Union{Nothing,Cuboid}=nothing, 
                SkipOptim::Bool=false, pnames::AbstractVector{<:StringOrSymb}=CreateSymbolNames(length(mle)), name::StringOrSymb="")
```

RパッケージdModに触発された条件グリッドを実装します。異なる`DataModel`を、同じ外部パラメータ値の集合ベクトルから読み取るパラメータ変換のベクトルを介して接続し、各ステップでそれらから各`DataModel`の個別のパラメータ構成を計算します。これにより、異なるデータセットを異なるモデルと簡単に接続し、モデル間で共有されるパラメータを用いて同時推論を行うことができます。
