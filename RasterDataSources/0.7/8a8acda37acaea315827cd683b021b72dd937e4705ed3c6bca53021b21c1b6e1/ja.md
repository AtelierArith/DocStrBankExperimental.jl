# RasterDataSources.jl

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://ecojulia.github.io/RasterDataSources.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://ecojulia.github.io/RasterDataSources.jl/dev) [![CI](https://github.com/EcoJulia/RasterDataSources.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/EcoJulia/RasterDataSources.jl/actions/workflows/CI.yml) [![codecov.io](http://codecov.io/github/ecojulia/RasterDataSources.jl/coverage.svg?branch=master)](http://codecov.io/github/ecojulia/RasterDataSources.jl?branch=master)

RasterDataSourcesは、ローカルで使用するためのラスターデータをダウンロードしたり、[Rasters.jl](https://github.com/rafaqz/Rasters.jl)のような他の空間データパッケージに統合するためのものです。このコレクションは主に生態学に関連するデータセットに焦点を当てていますが、他の科学とのクロスオーバーも多くあります。

現在のソースには以下が含まれます：

|    Source |                                      URL |                                   Status |
| ---------:| ----------------------------------------:| ----------------------------------------:|
|    CHELSA |               https://chelsa-climate.org |        BioClim, BioClimPlus, and Climate |
| WorldClim |                https://www.worldclim.org | Climate, Weather, BioClim, and Elevation |
|  EarthEnv |                  http://www.earthenv.org |       LandCover and HabitatHeterogeneity |
|      AWAP | http://www.bom.gov.au/jsp/awap/index.jsp |                                 Complete |
|      ALWB |   http://www.bom.gov.au/water/landscape/ |                                 Complete |
|      SRTM |          https://www2.jpl.nasa.gov/srtm/ |                                 Complete |
|     MODIS |                   https://modis.ornl.gov |                          Complete (beta) |

データセットの追加が必要な場合は、問題をオープンしてください。または、可能な限り他のデータセットの形式に従ってプルリクエストをオープンしてください。

## データの取得

使用は一般的に`getraster`メソッドを介して行われます - これは、ローカルに利用可能でない場合はラスターデータソースをダウンロードし、単にラスターファイルのパスを返します：

```julia
julia> using RasterDataSources

julia> getraster(WorldClim{Climate}, :wind; month=1:12)
12-element Array{String,1}:
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_01.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_02.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_03.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_04.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_05.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_06.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_07.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_08.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_09.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_10.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_11.tif"
 "/home/user/Data/WorldClim/Climate/wind/wc2.1_10m_wind_12.tif"
```

## インストールとセットアップ

通常通りにインストールします：

```julia
] add RasterDataSources
```

データをダウンロードするには、保存先のフォルダーを指定する必要があります。これは、環境変数`RASTERDATASOURCES_PATH`に割り当てることで行えます：

```julia
ENV["RASTERDATASOURCES_PATH"] = "/home/user/Data/"
```

これは、`startup.jl`ファイルやシステム環境に入れることができます。

RasterDataSourcesは、Timothée Poisotによる`SimpleSDMDataSoures.jl`パッケージのコードに基づいています。
