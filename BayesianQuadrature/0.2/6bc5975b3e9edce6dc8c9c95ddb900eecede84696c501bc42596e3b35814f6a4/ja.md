```
BayesQuad(k::Kernel; l=1.0, σ::Real=1.0)
```

与えられた `BayesQuadModel` と `Sampler` に対してベイズ積分を推定するためのツールです。

`BayesQuad` は確率分布 `p(I)` を推定します。ここで I = ∫ f(x) p(x) dx です。

## 引数

  * `k::Kernel` : `KernelFunctions.jl` からのカーネルで、カーネルは合成できません。

## キーワード引数

  * `l` : カーネルの長さスケール。次のいずれかです：

      * `Real` : 等方カーネル
      * `AbstractVector` : ARDカーネル（次元ごとの長さスケール）
      * `LowerTriangular` : 入力の線形変換
  * `σ` : カーネルの分散（`k(x,x') -> σ * k(x,x')`）

注意：もし `k` がすでに分散および/または変換を持っている場合、これらは自動的に抽出され、指定されたキーワード引数に置き換えられます。
