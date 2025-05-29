```
function combineinds(inds::Vector{Index};
                     maxdim::Union{Nothing, Int} = nothing, 
                     maxqnblocks::Union{Nothing, Int} = nothing,
                     kwargs...)
```

`Index`のベクトルを1つに結合します（ITensors.jlの`combiner`のように）。`maxdim`は出力`Index`の最大次元を、`maxqnblocks`は出力`Index`に保持する最大QNブロック数を表します。
