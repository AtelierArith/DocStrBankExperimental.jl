```
ardca(filename::String; kwds...)
```

`filename`のfastaアライメントで[`ardca`](@ref)を実行します。

2つの`struct`を返します：`::ArNet`（推定されたハイパーパラメータを含む）と`::ArVar`。

オプションの引数：

  * `max_gap_fraction::Real=0.9` シーケンス内の挿入の最大割合
  * `remove_dups::Bool=true` `true`の場合、重複したシーケンスを削除します
  * `theta=:auto` `:auto`の場合、自動的に再重み付けを計算します。それ以外の場合は、`0 ≤ theta ≤ 1`の`Float64`値を設定します
  * `lambdaJ::Real=0.01` 結合L₂正則化パラメータ（ラグランジュ乗数）
  * `lambdaH::Real=0.01` フィールドL₂正則化パラメータ（ラグランジュ乗数）
  * `pc_factor::Real=1/size(Z,2)` `p0`の計算のための擬似カウント因子、シーケンスの数の逆数がデフォルトです。
  * `epsconv::Real=1.0e-5` 最小化における収束値
  * `maxit::Int=1000` 最小化における最大反復回数
  * `verbose::Bool=true` `false`に設定すると、`stdout`への収束情報の印刷を停止します
  * `method::Symbol=:LD_LBFGS` 最適化戦略、他のオプションについては[`NLopt.jl`](https://github.com/JuliaOpt/NLopt.jl)を参照してください
  * `permorder::Union{Symbol,Vector{Ti}}=:ENTROPIC` 順列の順序。可能な値は`:NATURAL,:ENTROPIC,:REV_ENTROPIC,:RANDOM`またはカスタム順列ベクトルです。

# 例

```
julia> arnet, arvar =  ardca("pf14.fasta", permorder=:ENTROPIC)
```
