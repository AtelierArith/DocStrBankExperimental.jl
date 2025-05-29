```
morris(performance::Function, L::Array{Float64,1}, U::Array{Float64,1}; 
    number_of_samples::Int64 = 1000) -> Array{Float64,2}
```

`morris` 関数は、モリス法を使用してグローバル感度分析を実行する `gsa` 関数のラッパーです。

### 引数

  * `performance::Function`: パラメータのベクトルを受け取り、スカラーのパフォーマンス指標を返す関数。
  * `L::Array{Float64,1}`: パラメータの下限のベクトル。
  * `U::Array{Float64,1}`: パラメータの上限のベクトル。
  * `number_of_samples::Int64`: 分析に使用するサンプルの数。

### 戻り値

  * 結果の行列で、最初の列は平均、2 番目の列は感度分析の分散です。
