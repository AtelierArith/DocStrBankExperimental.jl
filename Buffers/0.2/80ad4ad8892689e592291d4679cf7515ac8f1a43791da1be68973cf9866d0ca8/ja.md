```
alloc!(buf, dims...; extend=true)
```

バッファ `buf` に指定された次元のテンソルを割り当てます。

テンソルは現在のオフセットから始まるバッファに割り当てられます。オフセットはテンソルの長さによって増加します。`extend=true` の場合、必要に応じてバッファが拡張されます。`ThreadsBuffer` の場合、テンソルは現在のスレッドのバッファに割り当てられます。

割り当てられたテンソルを返します。

```julia
julia> buf = Buffer(100000)
julia> A = alloc!(buf, 10, 10, 20) # 10x10x20 テンソル
julia> B = alloc!(buf, 10, 10, 10) # A の後に始まる 10x10x10 テンソル
julia> C = alloc!(buf, 10, 20) # B の後に始まる 10x20 テンソル
julia> rand!(B)
julia> rand!(C)
julia> An = neuralyze(A) # 起源のないテンソル
julia> @tensor An[i,j,k] = B[i,j,l] * C[l,k]
```
