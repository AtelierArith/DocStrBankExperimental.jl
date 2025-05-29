```
nc_string2char(x::Array{String})
```

Juliaの`String`配列を`Array{ASCIIChar}`に変換し、`NC_CHAR`型のNetCDF変数に書き込むことができるようにします。
