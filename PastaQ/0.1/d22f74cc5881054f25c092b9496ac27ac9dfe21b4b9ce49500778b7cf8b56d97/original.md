```
writesamples(data::Matrix{Int},
             [model::Union{MPS, MPO, LPDO, Nothing},]
             output_path::String)
```

Save data and model on file:

# Arguments:

  * `data`: array of measurement data
  * `model`: (optional) MPS, MPO, or Choi
  * `output_path`: path to file
