```
P = kp_block_jacobi(A)
```

KrylovソルバーをGPUアーキテクチャ上で加速するためのブロック・ジャコビ前処理器を構築します。

この前処理器は、NVIDIA、AMD、およびIntelのGPUに保存されたCSRまたはCSC形式のスパース行列と互換性があります。また、CSC形式のCPUでも動作します。

#### 入力引数

  * `A`: 対角ブロックが抽出されるCPUまたはGPU上の正方形スパース行列。

#### 出力引数

  * `P`: `AbstractKrylovPreconditioner`型の前処理器。
