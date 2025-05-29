```
ntt!(vec::CuVector{T}, dest::CuVector{T}, plan::NTTPlan{T}, bitreversedoutput::Bool = false) where T<:Union{Int32, Int64, UInt32, UInt64}
```

Takes the NTT according to `plan` of `vec`, storing the result in `dest`. 

# Arguments:

  * `vec`: Source vector of NTT.
  * `dest`: Destination vector of NTT.
  * `plan`: NTTPlan with ntt information. See `plan_ntt()` for generating plans.
  * `bitreversedoutput`: Bool determining whether output is in bit-reversed order. Defaults to false.

If `vec` and `dest` are the same, and `bitreversedoutput` is true, then the NTT is done in-place. As a shortcut, an overload is provided:

```jldoctest
ntt!(vec::CuVector, plan::NTTPlan, bitreversedoutput::Bool = false)
```
