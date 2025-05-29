```
Lon, Lat, Depth = lonlatdepth_grid(Lon::Any, Lat::Any, Depth:Any)
```

1Dベクトルまたは数値から`Lon`、`Lat`、`Depth`の3D配列を作成します。

# 例 1: 3Dグリッドを作成

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10:20,30:40,(-10:-1)km);
julia> size(Lon)
(11, 11, 10)
```

# 例 2: 指定した深さで2Dのlon/latグリッドを作成

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10:20,30:40,-50km);
julia> size(Lon)
(11, 11)
```

# 例 3: 指定した緯度で2Dのlon/depthグリッドを作成

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10:20,30,(-10:-1)km);
julia> size(Lon)
(11, 11)
```

# 例 4: 指定したlon/latポイントで1Dの垂直線を作成

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10,30,(-10:-1)km);
julia> size(Lon)
(10, )
```
