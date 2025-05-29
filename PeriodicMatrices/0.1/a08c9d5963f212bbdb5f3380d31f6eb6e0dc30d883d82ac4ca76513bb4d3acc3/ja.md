```
 phess!(A::Array{Float64,3}, ilh::Tuple(Int,Int) = (1, size(A,1)); kwargs...) -> (H, Z, ihess)
```

`phess(A; kwargs...)` と同様ですが、入力行列 `A` を作業領域として使用し、範囲 `ilh = (ilo, ihi)` を指定します。これにより、すべての行列 `A(j), j = 1, ..., p` がすでに行と列 `1:ilo-1` および `ihi+1:n` において周期的ヘッセンベルグ形式になっています。ここで、`n` は `A` の最初の次元です。
