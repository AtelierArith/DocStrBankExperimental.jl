```
ncsave(f::AbstractString, compress, options=(;); dims, kw...)
```

## 引数

  * `compress`: 0~10, 0は圧縮しないことを意味し、10は最大圧縮で、デフォルトは1
  * `options`: `nc_write!`への他のキーワード引数

## 例

```julia
dims = (; x = 1:10, y = 1:10)
ncsave("test.nc", true; dims, SM=rand(10, 10), SPI=rand(Float32, 10, 10))

# 上書き
ncsave("test.nc", true, (; overwrite=true); 
  dims, SM=rand(10, 10), SPI=rand(Float64, 10, 10))

dims = (; x = 1:10, y = 1:10, z = 1:10)
ncsave("test.nc"; dims, SM3=rand(10, 10, 10))
```
