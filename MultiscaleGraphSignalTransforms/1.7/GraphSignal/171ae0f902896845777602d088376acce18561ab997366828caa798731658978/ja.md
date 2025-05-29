```
G = gpath(N, f, name)
```

長さ `N` の1次元パスのためのGraphSigオブジェクトを生成します

### 入力引数

  * `N::Int`: パスの長さ
  * `f::Matrix{Float64}`: 使用する信号
  * `name::String`: GraphSigオブジェクトの名前

### 出力引数

  * `G::GraphSig`: 長さ `N` の1次元パスを表すGraphSigオブジェクト
