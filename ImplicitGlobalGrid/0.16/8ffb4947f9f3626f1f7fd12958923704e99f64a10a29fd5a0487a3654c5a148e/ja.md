```
gather!(A, A_global)
gather!(A, A_global; root=0)
```

!!! note "Advanced"
    ```
    gather!(A, A_global, comm; root=0)
    ```


配列 `A` を MPI プロセスの直交グリッドの各メンバーからルートプロセス（デフォルト: `0`）の1つの大きな配列 `A_global` に集めます。グローバル配列のサイズ `size(A_global)` は、`size(A)` と `dims` の積と等しくなければなりません。ここで、`dims` は直交グリッドの各次元のプロセス数であり、[`init_global_grid`](@ref) で定義されています。

!!! note "Advanced"
    引数 `comm` が指定されている場合、このコミュニケーターが集約操作に使用され、そこから `dims` が抽出されます。


!!! note "Memory requirements"
    グローバル配列のメモリはルートプロセスでのみ割り当てる必要があり、他のプロセスでは引数 `A_global` を `nothing` にすることができます。

