```
mutable struct KeplerGLMap 
    datasets::Vector{AbstractKeplerGLData}
    config::Dict{Symbol, Any}
    info::Dict{Symbol, Any}
    window::Dict{Symbol, Any}
end
```

マップを描画するためのすべての情報を含む型です。 `config` と `info` は、Kepler.gl が内部で使用するマップ JSON シリアル化と同じ構造です。 `datasets` は、レイヤーが描画するデータを含む [`AbstractKeplerGLData`](@ref) のインスタンスです。 `window` は、ウィンドウサイズ、マップを中央に配置するかどうかなどの情報を含む、Kepler.gl では使用されない追加情報です。
