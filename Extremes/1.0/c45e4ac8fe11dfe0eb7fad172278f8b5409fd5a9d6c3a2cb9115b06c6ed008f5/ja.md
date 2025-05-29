```
gumbelfit(y,
    initialvalues,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}()
    )
```

ガンベルパラメータを推定します。

# 引数

  * `y::Vector{<:Real}`: ブロック最大値のベクトル。
  * `initialvalues::Vector{<:Real}`: パラメータ初期値のベクトル。
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: ロケーションパラメータの共変量。
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: ログスケールパラメータの共変量。
