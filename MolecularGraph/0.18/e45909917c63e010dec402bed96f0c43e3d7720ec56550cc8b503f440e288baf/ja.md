```
sdftomol(::Type{T}, io::IO) -> T
sdftomol(io::IO) -> SDFMolGraph
sdftomol(::Type{T}, path::AbstractString) -> T
sdftomol(path::AbstractString) -> SDFMolGraph
```

SDFile（.sdfまたは.mol）を読み込み、指定された型の分子オブジェクトに解析します。指定された引数は、ファイル入力ストリームまたはファイルパスである必要があります。
