```
psreduc_reg(A) -> (M, N)
```

`p`次元の矩形行列のベクトル `A` に対して、`N` が可逆であり、`M-λN` が正則である行列ペア `(M, N)` を決定します。ここで、`M-λN` の固有値は、正方行列の積 `A(p)*A(p-1)*...*A(1)` の固有値と同じであり、`A(i)` は `A[i]` に含まれています。行列 `M` と `N` を決定するために、[1] の高速削減法を利用します。

[1] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
