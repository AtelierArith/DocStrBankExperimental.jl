```
bpf_data!(x::AbstractVecOrMat; bpf=get_bpf())
```

Bandpass (or low-pass or high-pass) filter vector or columns of matrix.

**Arguments:**

  * `x`:   data vector or matrix
  * `bpf`: (optional) filter object

**Returns:**

  * `nothing`: `x` is mutated with filtered data
