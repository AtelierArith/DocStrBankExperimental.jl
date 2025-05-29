```
fused_dense_bias_activation(σ::F, weight::AbstractMatrix, x::AbstractMatrix,
    b::Optional{<:AbstractVector}) where {F}
```

`σ.(weight * x .+ b)`を可能な限り最適な実装で計算します。現在の実装は、複数の操作のために出力バッファを再利用することで再割り当てを最小限に抑えることを試みています。

## 引数

  * `σ`: 活性化関数
  * `weight`: 重み行列
  * `x`: 入力行列
  * `b`: バイアスベクトル（`nothing`にすることも可能）

## 実装に関する注意

  * 入力のいずれかが、setindexingをサポートしていない場合（すなわち不変配列）、一般的な非変異実装にフォールバックします。
  * ChainRules互換のADバックエンドまたは変異をサポートするバックエンドに対しては、最大のメモリ再利用と操作の融合が保証されます。`Tracker`や`ReverseDiff`のようなバックエンドは、一般的な実装にフォールバックします。
  * CUDA配列の場合、cuBLASLtを介して特別な融合実装を使用します。
  * 小さなCPU配列の場合、LoopVectorization.jlを使用します。`x86_64`では、中サイズの行列に対してOctavianを使用します。これは、特別なBLAS実装がロードされている場合（現在は`MKL`、`AppleAccelerate`、および`BLISBLAS`）にオーバーライドされます。

!!! tip "Load `Octavian.jl`

```
`Octavian.jl`をロードすると、入力サイズに基づいて異なるバックエンドを使用するポリアルゴリズムが有効になります。
```
