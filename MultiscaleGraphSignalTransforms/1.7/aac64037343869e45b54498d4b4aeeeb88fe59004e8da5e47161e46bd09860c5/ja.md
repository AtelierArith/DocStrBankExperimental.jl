```
(pm,v) = partition_fiedler(W; method, v)
```

グラフの頂点をFiedlerベクトルに従って分割します

### 入力引数

  * `W::SparseMatrixCSC{Float64,Int}`: エッジ重み行列
  * `method::Symbol`: 使用する分割方法 (:L または :Lrw など ...)
  * `v::Vector{Float64}`: `v`がヌルベクトルの場合に供給されるFiedlerベクトル

### 出力引数

  * `pm::Vector{Int}`: 1と-1のベクトル
  * `v::Vector{Float64}`: グラフ分割に使用されるFiedlerベクトル

著作権 2015 カリフォルニア大学の理事会

実装者: ジェフ・イリオン (アドバイザー: 斉藤直樹博士) 翻訳および改訂: 斉藤直樹, 2017年2月9日
