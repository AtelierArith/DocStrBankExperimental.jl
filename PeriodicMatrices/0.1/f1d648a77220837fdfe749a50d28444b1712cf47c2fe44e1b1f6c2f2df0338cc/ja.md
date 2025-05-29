```
psreduc_reg(A,E) -> (M, N)
```

`n×n×p` 配列 `(A,E)` のペアに対して、`M-λN` が正則である行列ペア `(M, N)` を決定します。ここで、`M-λN` の固有値は、商行列積 `inv(E(p))*(A(p)*inv(E(p-1))*A(p-1)*...*inv(E(1))*A(1)` の固有値と同じです。ここで、`A(i)` は `A[:,:,i]` に含まれ、`E(i)` は `E[:,:,i]` に含まれます。`M` と `N` を決定するために、[1] の高速削減法を利用します。

[1] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
