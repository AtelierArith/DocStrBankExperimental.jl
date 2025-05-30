# リスケール

ベクトルを「非標準化」するためにリスケールします。これは scale!() の逆です。

```julia
rescale(x, xbar, xstd)

```

# 拡張ヘルプ

### 必要な引数

```julia
* `x::Vector{Float64}`                 : リスケールされるベクトル
* `xbar`                               : リスケーリングのための平均値
* `xstd`                               : リスケーリングのための標準偏差
```

### 戻り値

```julia
* `result::AbstractVector`             : リスケールされたベクトル
```
