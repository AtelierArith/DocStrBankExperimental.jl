# rescale

ベクトルを「非標準化」するために再スケーリングします。これは、scale!()の逆です。

```julia
rescale(x, xbar, xstd)

```

# 拡張ヘルプ

### 必要な引数

```julia
* `x::Vector{Float64}`                 : 再スケーリングされるベクトル
* `xbar`                               : 再スケーリングのための平均値
* `xstd`                               : 再スケーリングのための標準偏差
```

### 戻り値

```julia
* `result::AbstractVector`             : 再スケーリングされたベクトル
```
