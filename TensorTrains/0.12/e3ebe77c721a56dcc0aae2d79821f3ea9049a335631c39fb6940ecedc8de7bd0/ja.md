```
TruncVUMPS{TI, TF} <: SVDTrunc
```

[`InfiniteUniformTensorTrain`](@ref) のターゲットボンドサイズ `d` への切り捨てを実行するために使用される型です。これは、MPSKit.jl の変分一様行列積状態 (VUMPS) アルゴリズムを使用します。

# フィールド

  * `d`: ターゲットボンド次元
  * `maxiter = 100`: VUMPS アルゴリズムの最大反復回数
  * `tol = 1e-14`: VUMPS アルゴリズムの許容誤差

```@example
p = rand_infinite_uniform_tt(10, 2, 2)
compress!(p, TruncVUMPS(5))
```
