```
hwp_gen(T;μ=0,σ=1)
```

ハスラーとホセインコウチャック（2020）による調和加重プロセスを使用して、長期記憶を持つ時系列を生成します。

# 引数

  * `T::Int`: 時系列の長さ
  * `μ::Float64`: 時系列の平均
  * `σ::Float64`: 時系列の標準偏差

# 出力

  * `x::Vector`: 長期記憶を持つ時系列

# 例

```julia-repl
julia> hwp_gen(100)
```
