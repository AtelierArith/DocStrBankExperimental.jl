```julia
calc_divergences(sys, evelo, bfvelo)

```

`evelo` と `bfvelo` を取得するために [`edgevelocities`](@ref) と [`bfacevelocities`](@ref) を使用して、sys.grid のノードに関連付けられた各ボロノイセルの速度場の発散を計算します。これは、各ボロノイセルごとにすべての `evelos` と `bfvelos` を合計することによって行われます。
