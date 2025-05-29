```
intt!(vec::CuVector{T}, dest::CuVector{T}, plan::INTTPlan{T}, bitreversedinput::Bool = false) where T<:Union{Int32, Int64, UInt32, UInt64}
```

Takes the INTT according to `plan` of `vec`, storing the result in `dest`. 

# Arguments:

  * `vec`: Source vector of INTT.
  * `dest`: Destination vector of INTT.
  * `plan`: INTTPlan with intt information. See `plan_ntt()` for generating plans.
  * `bitreversedinput`: Bool determining whether input is in bit-reversed order. Defaults to false.

If `vec` and `dest` are the same, and `bitreversedoutput` is true, then the INTT is done in-place. As a shortcut, an overload is provided:

```jldoctest
intt!(vec::CuVector, plan::INTTPlan, bitreversedinput::Bool = false)
```
