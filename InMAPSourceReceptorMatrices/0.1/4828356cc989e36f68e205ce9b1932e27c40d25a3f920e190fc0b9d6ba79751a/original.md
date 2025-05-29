```
connect_to_isrm!(; region="us-east-2", creds = nothing, url="s3://inmap-model/isrm_v1.2.1.zarr/")
```

Connects to AWS, opens the INMAP source receptor matrix with `zopen` (from Zarr.jl)
