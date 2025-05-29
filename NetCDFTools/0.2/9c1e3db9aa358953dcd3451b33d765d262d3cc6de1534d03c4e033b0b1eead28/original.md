```
ncsave(f::AbstractString, compress, options=(;); dims, kw...)
```

## Arguments

  * `compress`: 0~10, 0代表不压缩, 10最大压缩，默认为1
  * `options`: other keyword arguments to `nc_write!`

## Examples

```julia
dims = (; x = 1:10, y = 1:10)
ncsave("test.nc", true; dims, SM=rand(10, 10), SPI=rand(Float32, 10, 10))

# overwrite
ncsave("test.nc", true, (; overwrite=true); 
  dims, SM=rand(10, 10), SPI=rand(Float64, 10, 10))

dims = (; x = 1:10, y = 1:10, z = 1:10)
ncsave("test.nc"; dims, SM3=rand(10, 10, 10))
```
