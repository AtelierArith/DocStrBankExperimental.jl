```
sds_gen(T::Int,d; t=0.5, μ=0, σ=1)
```

長期記憶パラメータ `d` と長さ `T` を持つ時系列を確率的持続ショックモデルを使用して生成します。

# 引数

  * `T::Int`: 時系列の長さ
  * `d::Float64`: 長期記憶パラメータ

# オプション引数

  * `t::Float64`: テーパー長
  * `μ::Float64`: 時系列の平均
  * `σ::Float64`: 時系列の標準偏差

# 出力

  * `x::Vector`: 長期記憶を持つ時系列

# 注意事項

テーパー長 `t` は、モデルの初期バイアスを回避するために事前にサンプリングされる時系列の割合です。参考文献: Parke (1999)

# 例

```julia-repl
julia> sds_gen(100,0.4)
```
