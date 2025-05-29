```
plan_ntt(len::Integer, p::Integer, npru::Integer; memoryefficient = false) -> Tuple{NTTPlan, INTTPlan}
```

Returns a NTTPlan, as well as the inverse INTTPlan to be used in  `ntt!()` and `intt!()`. Type of NTT is determined by p, which must be in `Union{Int32, Int64, UInt32, UInt64}`.

# Arguments:

  * `len`: Length of NTT (must be power of 2)
  * `p`: Characteristic of field to perform NTT in.
  * `npru`: len-th primitive root of unity of `p`. No validation is done, see `primitive_nth_root_of_unity()` to generate.
  * `memoryefficient`: Boolean to determine whether or not to generate root of unity table. If false, NTT will be slower but use half the memory.
