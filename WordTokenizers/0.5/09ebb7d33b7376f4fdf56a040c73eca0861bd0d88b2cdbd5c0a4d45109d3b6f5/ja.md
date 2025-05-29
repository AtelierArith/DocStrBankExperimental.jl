```
load(ty::Type{T}, filenum::Int=1; unk_token="<unk>") where T<:PretrainedTokenizer
```

`DataDeps` からファイルを読み込むことで `SentencePieceModel` を初期化するために使用します。

# 例

```julia-repl
julia> spm = load(ALBERT_V1)
```
