```
save_rand_design_job(d_rand::RandDesign, backend::String, job_counts::Union{Vector{Matrix{UInt8}}, Vector{Dict{String, Int}}}, job_idx::Integer)
```

Saves the job counts data `job_counts` with index `job_idx` for the randomised experimental design `d_rand` with the filename determined by the supplied `backend`.
