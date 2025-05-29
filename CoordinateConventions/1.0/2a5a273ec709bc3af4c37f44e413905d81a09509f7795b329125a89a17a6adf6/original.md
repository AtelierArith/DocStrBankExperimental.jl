```
transform_cocos(cc_in::Union{Int,COCOS}, cc_out::Union{Int,COCOS};
                sigma_Ip = nothing, sigma_B0=nothing,
                ld = (1,1), lB = (1,1), exp_mu0 = (0,0)) -> Dict
```

Returns a dictionary of the multiplicative factors to transform COCOS from cc*in to cc*out

Arguments:

  * sigma_Ip::Union{NTuple{2,Int},Nothing} - A tuple of the (Input, Output) current sign or nothing
  * sigma_B0::Union{NTuple{2,Int},Nothing} - A tuple of the (Input, Output) toroidal field sign or nothing
  * ld::NTuple{2,<:Real} - A tuple of the (Input, Output) length scale factor. Default = (1,1)
  * lB::NTuple{2,<:Real} - A tuple of the (Input, Output) magnetic field scale factor. Default = (1,1)
  * exp_mu0::NTuple{2,<:Real} - A tuple of the (Input, Output) mu0 exponent (0, 1). Default = (0,0)
