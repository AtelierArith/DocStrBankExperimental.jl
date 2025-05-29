```
bpf_data(x::AbstractVector; bpf=get_bpf())
```

Bandpass (or low-pass or high-pass) filter vector.

**Arguments:**

  * `x`:   data vector (e.g., magnetometer measurements)
  * `bpf`: (optional) filter object

**Returns:**

  * `x_f`: data vector, filtered
