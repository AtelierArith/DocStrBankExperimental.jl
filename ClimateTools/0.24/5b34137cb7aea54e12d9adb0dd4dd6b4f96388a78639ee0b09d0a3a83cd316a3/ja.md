```
ClimGrid{A <: AxisArray}
```

気候予測のnetCDFファイルのメモリ内表現。構造体 ClimGrid

data::AxisArray # データ

longrid::AbstractArray{N,2} where N # 経度グリッド

latgrid::AbstractArray{N,2} where N # 緯度グリッド

msk::Array{N, 2} where N # データマスク（NaNsと1.0）

grid_mapping::Dict#{String, Any} # ネイティブグリッドのバインディング

dimension_dict::Dict

model::String

frequency::String # 日、月、年

experiment::String # 歴史的、RCP4.5、RCP8.5など

run::String

project::String # CORDEX、CMIP5など

institute::String # UQAM、DMIなど

filename::String # 元のファイルのパス

dataunits::String # セルシウス、ケルビンなど

latunits::String # 緯度座標単位

lonunits::String # 経度座標単位

variable::String # 変数の種類（すなわち、「typeofvar」と同じである可能性があるが、インデックスを計算する際に変更される）

typeofvar::String # 変数の種類（例：tasmax、tasmin、pr）

typeofcal::String # カレンダーの種類

timeattrib::Dict # 時間属性（例：...からの日数）

varattribs::Dict # 変数属性辞書

globalattribs::Dict # グローバル属性辞書

end
