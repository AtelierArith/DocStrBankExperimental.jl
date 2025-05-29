```
mappingParameters( T::DataType=Float64;
                   x_lim::Vector{Float64}   = [-1.0, -1.0],
                   y_lim::Vector{Float64}   = [-1.0, -1.0],
                   z_lim::Vector{Float64}   = [-1.0, -1.0],
                   center::Vector{Float64}  = [-1.0, -1.0, -1.0],
                   x_size::Float64          =  -1.0,
                   y_size::Float64          =  -1.0,
                   z_size::Float64          =  -1.0,
                   pixelSideLength::Float64 =  -1.0,
                   Npixels::Int64           =   0)
```

sphからグリッドへのマッピングのためのパラメータオブジェクト。`*_lim`または`center`と`*_size`のいずれかを定義します。解像度は`pixelSideLength`または`Npixels`によって定義されます。
