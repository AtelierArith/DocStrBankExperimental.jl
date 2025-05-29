```
SparseAssembler(handle::Union{PyObject, <:Integer}, n::Union{PyObject, <:Integer}, tol::Union{PyObject, <:Real}=0.0)
```

スパース行列のために `row`, `col`, `val` を蓄積するための SparseAssembler を作成します。

  * `handle`: スパース行列を作成するための整数ハンドル。ハンドルがすでに存在する場合、`SparseAssembler` は既存のスパース行列ハンドルを返します。異なるスパース行列を作成する場合、ハンドルは異なる必要があります。
  * `n`: スパース行列の行数。
  * `tol` (オプション): 許容誤差。`SparseAssembler` は `tol` より小さい値をゼロとして扱います。

# 例 1

```julia
handle = SparseAssembler(100, 5, 1e-8)
op1 = accumulate(handle, 1, [1;2;3], [1.0;2.0;3.0])
op2 = accumulate(handle, 2, [1;2;3], [1.0;2.0;3.0])
J = assemble(5, 5, [op1;op2])
```

`J` は [`SparseTensor`](@ref) オブジェクトになります。

# 例 2

```julia
handle = SparseAssembler(0, 5)
op1 = accumulate(handle, 1, [1;2;3], ones(3))
op2 = accumulate(handle, 1, [3], [1.])
op3 = accumulate(handle, 2, [1;3], ones(2))
J = assemble(5, 5, [op1;op2;op3]) # op1, op2, op3 は並行しています
Array(run(sess, J))≈[1.0  1.0  2.0  0.0  0.0
                1.0  0.0  1.0  0.0  0.0
                0.0  0.0  0.0  0.0  0.0
                0.0  0.0  0.0  0.0  0.0
                0.0  0.0  0.0  0.0  0.0]
```
