```
extract_recurrences_joint(data_source::Vector{Float64}, data_source2::Vector{Float64},
    motifs_dict::Dict{String, Vector}; num_windows::Int64 = 3)

    This function returns x and y coordinates for a given window 
        considering start and size of each motif detected from 
        two time-series in joint-recurrence matrices .
```

The y coordinates are the values from data provided by the user. 
