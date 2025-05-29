```julia
compareRevisions(t, previous::Dict{String,Any}, current::Dict{String,Any}) where {T<:BitemporalPostgres.ComponentRevision} 
    compare 対応するリビジョン要素を比較し、等しい場合は何も返さず、そうでない場合は両方のペアを返します。
```
