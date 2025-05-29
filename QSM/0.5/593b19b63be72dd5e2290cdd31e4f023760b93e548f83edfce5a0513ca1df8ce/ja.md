```
bet(
    mag::AbstractArray{<:Real, 3},
    vsz::NTuple{3, Real},
    betargs::AbstractString = "-m -n -f 0.5"
) -> Array{Bool, 3}
```

FSLのbetへのインターフェース。

### 引数

  * `mag::AbstractArray{<:Real, 3}`: 大きさ画像
  * `vsz::NTuple{3, Real}`: ボクセルサイズ
  * `betargs::AbstractString = "-m -n -f 0.5"`: betオプション

### 戻り値

  * `Array{Bool, 3}`: バイナリ脳マスク
