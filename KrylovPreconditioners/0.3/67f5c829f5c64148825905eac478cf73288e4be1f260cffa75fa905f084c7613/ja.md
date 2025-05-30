```
P = kp_ic0(A)
```

不完全LU前処理子をゼロフィルインで構築します – ILU(0) は、GPUアーキテクチャ上でKrylovソルバーを加速するためのものです。

この前処理子は、NVIDIAおよびAMD GPUに保存されたCSRまたはCSC形式のスパース行列と互換性があります。

#### 入力引数

  * `A`: 不完全に因子分解するGPU上の正方スパース行列。

#### 出力引数

  * `P`: `AbstractKrylovPreconditioner`型の前処理子。
