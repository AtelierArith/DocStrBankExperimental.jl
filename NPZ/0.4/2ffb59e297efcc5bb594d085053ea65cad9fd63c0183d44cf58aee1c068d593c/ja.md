```
npzwrite(filename::AbstractString, x)
```

変数 `x` を `npy` ファイル `filename` に書き込みます。 `numpy` とは異なり、拡張子 `.npy` は `filename` に追加されません。

!!! warn "警告"
    同じ名前の既存のファイルは上書きされます。


# 例

```julia
julia> npzwrite("abc.npy", zeros(3))

julia> npzread("abc.npy")
3-element Array{Float64,1}:
 0.0
 0.0
 0.0
```
