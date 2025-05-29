```
arfima_gen(T::Int, μ::Real, AR::Array, d::Real, MA::Array; σ=1)
```

長期記憶パラメータ `d` と長さ `T` を持つ時系列を ARFIMA(p,d,q) モデルを使用して生成します。

# 引数

  * `T::Int`: 時系列の長さ
  * `μ::Float64`: 時系列の平均
  * `AR::Array`: AR係数
  * `d::Float64`: 分数差分パラメータ
  * `MA::Array`: MA係数

# オプション引数

  * `σ::Float64`: 時系列の標準偏差

# 出力

  * `x::Vector`: 長期記憶を持つ時系列

# 注意事項

このコードは、[Carlos Vladimir Rodríguez Caballero (2023)](https://www.mathworks.com/matlabcentral/fileexchange/53301-arfima-p-d-q) の関数 `dgp_arfima.m` に触発されています。

# 例

```julia-repl
julia> arfima_gen(100, 0, [0.2; -0.5], 0.4, [-0.3; 0.1]])
```
