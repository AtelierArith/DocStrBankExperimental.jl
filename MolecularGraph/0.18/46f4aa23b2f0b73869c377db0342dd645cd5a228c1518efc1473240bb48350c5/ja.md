```
rxntoreaction(::Type{T}, io::IO) -> T
rxntoreaction(io::IO) -> Reaction{SDFMolGraph}
rxntoreaction(::Type{T}, path::AbstractString) -> T
rxntoreaction(path::AbstractString) -> Reaction{SDFMolGraph}
```

RXNファイルを読み込み、指定された型の反応オブジェクトに解析します。指定された引数は、ファイル入力ストリームまたはファイルパスである必要があります。
