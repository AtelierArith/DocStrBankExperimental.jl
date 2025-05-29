```
sobol(performance::Function, L::Array{Float64,1}, U::Array{Float64,1}; 
    number_of_samples::Int64 = 1000, orders::Array{Int64,1} = [0, 1, 2])
```

`sobol` 関数は、Sobol メソッドを使用してグローバル感度分析を実行する `gsa` 関数のラッパーです。

### 引数

  * `performance::Function`: パラメータのベクトルを受け取り、スカラーのパフォーマンスメトリックを返す関数。
  * `L::Array{Float64,1}`: パラメータの下限のベクトル。
  * `U::Array{Float64,1}`: パラメータの上限のベクトル。
  * `number_of_samples::Int64`: 分析に使用するサンプルの数。
  * `orders::Array{Int64,1}`: 計算する感度の次数。

### 戻り値

  * `SobolResult` オブジェクト。
