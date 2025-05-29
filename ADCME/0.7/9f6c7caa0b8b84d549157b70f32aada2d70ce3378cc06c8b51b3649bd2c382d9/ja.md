```
TR_BDF2(D0::Union{SparseTensor, SparseMatrixCSC}, 
    D1::Union{SparseTensor, SparseMatrixCSC}, 
    Δt::Float64)
```

TR-BDF2（台形則と二次後方差分法）ハンドラをDAEのために構築します。

$$
D_1 \dot y + D_0 y = f
$$

この構造体はファンクタであり、1ステップのシミュレーションを実行します。

```
(tr::TR_BDF2)(y::Union{PyObject, Array{Float64, 1}}, 
    f1::Union{PyObject, Array{Float64, 1}}, 
    f2::Union{PyObject, Array{Float64, 1}}, 
    f3::Union{PyObject, Array{Float64, 1}})
```

ここで `f1`、`f2`、および `f3` は、時間ステップ $n$、$n+\frac12$、および $n+1$ における右辺に対応します。

また、バッチ処理された `F` を `(2NT+1) × DOF` 配列として渡すこともできます。

```
(tr::TR_BDF2)(y0::Union{PyObject, Array{Float64, 1}}, 
    F::Union{PyObject, Array{Float64, 2}})
```

出力はサイズ `(NT+1) × DOF` の全解となります。

!!! info
    このスキームは、n = 0, 1, ... の場合に次の形を取ります。 $\begin{aligned} D_1(y^{n+\frac12}-y^n) = \frac12\frac{\Delta t}{2}\left(f^{n+\frac12} + f^n - D_0 \left(y^{n+\frac12} + y^n\right)\right)\\ \left(\frac{\Delta t}{2}\right)^{-1} D_1 \left(\frac32y^{n+1} - 2y^{n+\frac12} + \frac12 y^n\right) + D_0 y^{n+1} = f^{n+1}\end{aligned}$


```
