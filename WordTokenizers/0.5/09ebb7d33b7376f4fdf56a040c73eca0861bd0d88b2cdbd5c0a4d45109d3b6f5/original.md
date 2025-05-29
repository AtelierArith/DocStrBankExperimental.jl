```
load(ty::Type{T}, filenum::Int=1; unk_token="<unk>") where T<:PretrainedTokenizer
```

use to initialize the `SentencePieceModel` by loading the file from `DataDeps`

# Example

```julia-repl
julia> spm = load(ALBERT_V1)
```
