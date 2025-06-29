```
fi_gen(T,d;μ=0,σ=1)
```

長期記憶パラメータ `d` と長さ `T` を持つ時系列を分数差分フィルタを使用して生成します。

# 引数

  * `T::Int`: 時系列の長さ
  * `d::Float64`: 分数差分パラメータ

# オプション引数

  * `μ::Float64`: 時系列の平均
  * `σ::Float64`: 時系列の標準偏差

# 出力

  * `x::Vector`: 長期記憶を持つ時系列

# 注意事項

生成には多重ディスパッチが使用されます：もし `d` が整数であれば、関数は一次またはゼロ差分の時系列を返します。詳細については `fracdiff` を参照してください。

# 例

```julia-repl
julia> fi_gen(100,0.4)
```
