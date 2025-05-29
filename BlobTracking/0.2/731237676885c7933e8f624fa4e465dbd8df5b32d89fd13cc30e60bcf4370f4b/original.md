```
trace(b::Blob)
```

Get the location trace of a blob. Use `tm = Matrix(t::Trace)` to get an N×2 matrix. Use `tm = replace(Float64.(tm), 0=>NaN)` to create a matrix with NaNs where there were missing measurements, this is useful for plotting since it creates a gap where the missing measurement was.
