push_chunk(outlet::StreamOutlet{T},            data::Matrix{T},            timestamp::Vector{Float64};            pushthrough = true)

Push a chunk of samples into the outlet with individual timestamps.

Each sample consists of the column of the matrix `data` such that size(data) = (M,N) where M is the channel count of the outlet, and N is the number of samples in the chunk.

# Arguments

-`timestamps`: Capture time of the sample, in agreement with `local_clock()`, if ommitted,                the current time is used.

# Keyword arguments

-`passthrough::Bool`: Whether to push the sample through to the receivers instead of                       buffering it with subsequent samples. Note that the chunk_size, if                       specified at outlet construction, takes precedence over the                       pushthrough flag.
