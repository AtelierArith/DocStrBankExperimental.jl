Use:   read*con(con::SeisCon;                  blocks::Array{Int,1} = Array(1:length(con)),                 prealloc*traces::Int = 50000)

Read 'blocks' out of 'con' into a preallocated array of size (ns x prealloc_traces).

If preallocated memory fills, it will be expanded again by 'prealloc_traces'.
