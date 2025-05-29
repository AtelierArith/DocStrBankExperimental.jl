````markdown
flatten_cross_section(V::GeoData)
この関数は、GeoData構造体を通る3D断面を取り、後の2D処理/プロットのために断面に沿った距離を計算します。
```julia-repl
julia> Lon,Lat,Depth   =   lonlatdepth_grid(10:20,30:40,(-300:25:0)km);
julia> Data            =   Depth*2;                # 一部のデータ
julia> Vx,Vy,Vz        =   ustrip(Data*3),ustrip(Data*4),ustrip(Data*5);
julia> Data_set3D      =   GeoData(Lon,Lat,Depth,(Depthdata=Data,LonData=Lon, Velocity=(Vx,Vy,Vz)));
julia> Data_cross      =   cross_section(Data_set3D, Start=(10,30),End=(20,40))
julia> x_profile        =   flatten_cross_section(Data_cross)
julia> Data_cross      =   addfield(Data_cross,"x_profile",x_profile)

````
