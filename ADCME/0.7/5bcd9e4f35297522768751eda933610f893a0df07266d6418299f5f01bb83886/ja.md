```
factorize(A::Union{SparseTensor, SparseMatrixCSC}, max_cache_size::Int64 = 999999)
```

$$
A
$$

をスパース行列の解法のために因数分解します。`max_cache_size`はC++カーネル内の最大キャッシュサイズを指定し、因数分解された行列の最大数を決定します。この関数は因数分解された行列を返し、基本的には`Tuple{SparseTensor, PyObject}`です。

# 例

```julia
A = sprand(10,10,0.7)
Afac = factorize(A) # 行列の因数分解
run(sess, Afac\rand(10)) # 因数分解なし、方程式を解く
run(sess, Afac\rand(10)) # 因数分解なし、方程式を解く
```
