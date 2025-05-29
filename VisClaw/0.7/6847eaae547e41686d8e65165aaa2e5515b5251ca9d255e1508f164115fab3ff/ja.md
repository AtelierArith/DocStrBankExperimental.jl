```
amrs = loadstorm(outputdir::AbstractString, filesequence::AbstractVector=0:0; kwargs...)
amrs = loadstorm(outputdir::AbstractString, fileid::Integer; kwargs...)
```

関数: ストームデータの時系列を読み込む。           キーワード引数は [`loadfortq`](@ref) に従います。           参照: [`loadfortt`](@ref).
