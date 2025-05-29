```
SeisDecimate(in; <keyword arguments>)
```

Apply random or regular decimation to a multidimensional array of data. Input and output have the same dimensions.

# Arguments

  * `in`: input data as 2D, or 3D,4D,5D tensors. The first dimension is time.

# Keyword arguments

  * `mode="random"`: decimation mode. Random is default, else decimates uniformly.
  * `perc=50`: percentage of traces equal to zero (decimated). Only for random mode
  * `incx1=1`: consecutive traces zeroed in first dimension. Only for regular decimation
  * `incx2=1`: consecutive traces zeroed in second dimension.
  * `incx3=1`: consecutive traces zeroed in third dimension.
  * `incx4=1`: consecutive traces zeroed in fourth dimension.

# Example

```julia
julia> d = SeisLinearEvents(); deci = SeisDecimate(d);
```

*Credits: Aaron Stanton,2017*
