```
ardca(Z::Array{Ti,2},W::Vector{Float64}; kwds...)
```

L×M アライメント `Z`（1,…,21 で数値的にエンコードされた）に対する自己回帰分析と、`M` 次元の正規化された重みベクトル `W`。

2 つの `struct` を返します: `::ArNet`（推定されたハイパーパラメータを含む）と `::ArVar`。

オプションの引数:

  * `lambdaJ::Real=0.01` 結合 L₂ 正則化パラメータ（ラグランジュ乗数）
  * `lambdaH::Real=0.01` フィールド L₂ 正則化パラメータ（ラグランジュ乗数）
  * `pc_factor::Real=0` `p0` の計算のための擬似カウント因子、デフォルトはシーケンスの数の逆数。
  * `epsconv::Real=1.0e-5` 最小化における収束値
  * `maxit::Int=1000` 最小化における最大反復回数
  * `verbose::Bool=true` `false` に設定すると、`stdout` に収束情報の印刷を停止します
  * `method::Symbol=:LD_LBFGS` 最適化戦略、他のオプションについては [`NLopt.jl`](https://github.com/JuliaOpt/NLopt.jl) を参照
  * `permorder::Union{Symbol,Vector{Ti}}=:ENTROPIC` 順列の順序。可能な値は `:NATURAL,:ENTROPIC,:REV_ENTROPIC,:RANDOM` またはカスタム順列ベクトルです。

# 例

```
julia> arnet, arvar= ardca(Z,W,lambdaJ=0,lambdaH=0,permorder=:REV_ENTROPIC,epsconv=1e-12);
```
