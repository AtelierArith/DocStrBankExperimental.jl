```
generate_ranked_partitions(data::Dict{String,<:Any}, results::Dict{String,<:Any})::Vector
```

Generate ranked robust partitions based on objective and mip_gap. For results of first iteration (single scenario considered) of outer problem, lower objective indicates more robutness to contingencies. For results of last iteration (multiple scenarios considered) of outer problem, lower objective indicates less scenarios were added to make partition robust to load uncertainty.
