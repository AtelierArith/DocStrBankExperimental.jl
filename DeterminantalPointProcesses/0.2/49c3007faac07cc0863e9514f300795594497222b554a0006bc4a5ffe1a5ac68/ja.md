```
DeterminantalPointProcess(L::AbstractMatrix; parallelize=false)
DeterminantalPointProcess(L::Eigen; parallelize=false)
```

対称行列 `L` が与えられた場合、`DeterminantalPointProcess` (DPP) を作成します。固有オブジェクトを直接渡すこともできます。

---

```
DeterminantalPointProcess(kernel::Kernel, X::AbstractVector; parallelize=false)
DeterminantalPointProcess(kernel::Kernel, X::AbstractMatrix; obsdim=1; parallelize=false)
```

基本コンストラクタと同様に、最初に観測 `X` に対して `kernel` を用いてカーネル行列を構築します。入力が `AbstractMatrix` の場合、行または列がサンプルを表すかを示すために `obsdim` 引数を渡すことができます（[KernelFunctions](https://juliagaussianprocesses.github.io/KernelFunctions.jl/stable/) のドキュメントを参照してください）。
