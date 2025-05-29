```
function convert_ocean_vars(raster::RasterStack, var_names::NamedTuple;
                            ref_pressure = nothing,
                            with_α = false,
                            with_β = false)
function convert_ocean_vars(raster::Rasterseries, var_names::NamedTuple;
                            ref_pressure = nothing,
                            with_α = false,
                            with_β = false)
```

海洋変数の深さ、実用塩分、潜在温度を圧力、絶対塩分、保守的温度に変換します。すべての変換は、TEOS-10のjulia実装[GibbsSeaWater.jl](https://github.com/TEOS-10/GibbsSeaWater.jl)を使用して行われます。圧力、絶対塩分、保守的温度、密度（その場またはユーザー定義の基準圧力に基づく）の変数を含む新しい`Raster`が返されます。圧力は緯度と深さに依存するため、新しい変数として追加されます。つまり、各経度、緯度、深さ、時間には圧力の変数があります。また、デフォルトでは*その場*の密度が計算される密度変数も計算されます。基準圧力での潜在密度は、キーワード引数`ref_pressure`を渡すことで計算できます。オプションのキーワード引数`with_α`と`with_β`を使用すると、熱膨張係数と塩分収縮係数（それぞれ）を計算して返される`RasterStack/Series`に追加できます。

潜在温度と実用塩分の変数名は、`(Sₚ = :salt_name, θ = :potential_temp_name)`の形式の`NamedTuple`として渡す必要があります。ここで、`:potential_temp_name`と`:salt_name`は`Raster`内の潜在温度と実用塩分の名前です。
