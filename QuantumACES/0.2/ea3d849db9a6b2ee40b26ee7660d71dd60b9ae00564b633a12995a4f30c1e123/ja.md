```
save_rand_design_job(d_rand::RandDesign, backend::String, job_counts::Union{Vector{Matrix{UInt8}}, Vector{Dict{String, Int}}}, job_idx::Integer)
```

ランダム化実験デザイン `d_rand` のために、指定された `backend` によって決定されるファイル名で、インデックス `job_idx` のジョブカウントデータ `job_counts` を保存します。
