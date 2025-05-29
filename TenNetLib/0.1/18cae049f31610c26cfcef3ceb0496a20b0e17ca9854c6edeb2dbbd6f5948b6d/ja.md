```
function indexintersection(inds1::Vector{Index}, inds2::Vector{Index};
                           maxdim::Union{Nothing, Int} = nothing,
                           maxqnblocks::Union{Nothing, Int} = nothing,
                           kwargs...)
```

2つの`Index`のベクトルの集合の交差を実行します。`maxdim`は出力`Index`の最大次元を、`maxqnblocks`は出力`Index`に保持する最大のQNブロック数を表します。
