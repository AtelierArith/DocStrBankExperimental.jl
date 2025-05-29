```
psreduc_reg(A) -> (M, N)
```

`n×n×p` 配列 `A` に対して、行列ペア `(M, N)` を決定します。ここで `N` は可逆であり、`M-λN` は正則で、`M-λN` の固有値は行列積 `A(p)*A(p-1)*...*A(1)` の固有値と同じである必要があります。ここで `A(i)` は `A[:,:,i]` に含まれています。行列 `M` と `N` を決定するために、[1] の構造を利用した高速削減法が使用されます。

[1] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
