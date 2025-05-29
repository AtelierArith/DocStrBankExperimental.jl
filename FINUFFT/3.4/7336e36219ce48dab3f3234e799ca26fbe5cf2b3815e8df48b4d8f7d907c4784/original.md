```
finufft_exec!(plan::finufft_plan{T},
              input::FINUFFT.InputArray{Complex{T}},
              output::FINUFFT.InputArray{Complex{T}}) where T <: finufftReal
```

Execute single or many-vector FINUFFT transforms in a plan, with output written to preallocated array. See `finufft_exec` for arguments.

`input` and `output` must be contiguous arrays.
