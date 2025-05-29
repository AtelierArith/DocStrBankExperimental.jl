```
amrs = loadsurface(outputdir::AbstractString, filesequence::AbstractVector; kwargs...)
amrs = loadsurface(outputdir::AbstractString, fileid::Integer; kwargs...)
```

関数: 水面の時系列を読み込む。           キーワード引数は [`loadfortq`](@ref) に従います。           参照: [`loadfortt`](@ref).
