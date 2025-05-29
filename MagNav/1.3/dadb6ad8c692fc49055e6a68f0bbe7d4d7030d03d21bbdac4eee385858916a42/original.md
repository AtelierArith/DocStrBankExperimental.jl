```
bpf_data(x::AbstractMatrix; bpf=get_bpf())
```

Bandpass (or low-pass or high-pass) filter columns of matrix.

**Arguments:**

  * `x`:   data matrix (e.g., Tolles-Lawson `A` matrix)
  * `bpf`: (optional) filter object

**Returns:**

  * `x_f`: data matrix, filtered
