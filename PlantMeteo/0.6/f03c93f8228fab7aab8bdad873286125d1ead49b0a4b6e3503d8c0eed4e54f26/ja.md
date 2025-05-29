```
read_weather(
    file[,args...];
    date_format = DateFormat("yyyy-mm-ddTHH:MM:SS.s"),
    hour_format = DateFormat("HH:MM:SS"),
    duration=nothing
)
```

気象ファイルを読み込みます。気象ファイルはCSV形式で、オプションでメタデータがコメント付きYAMLとしてヘッダーに含まれています。列名**および単位**は、[`Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/#PlantMeteo.Atmosphere)のフィールドと正確に一致する必要があります。そうでない場合、ユーザーは引数（`args`）として`DataFrames.jl`形式で変換を提供する必要があります。すなわち：

  * `:var_name => (x -> x .+ 1) => :new_name`: 変数`:var_name`は関数`x -> x .+ 1`によって変換され、`:new_name`に名前が変更されます。
  * `:var_name => :new_name`: 変数`:var_name`は`:new_name`に名前が変更されます。
  * `:var_name`: 変数`:var_name`はそのまま保持されます。

# 注意

ファイル内で見つかった変数は、変換されない場合はそのまま使用され、他の変数から再計算されることはありません。すべての変数が[`Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/#PlantMeteo.Atmosphere)構造と同じ単位であることを確認してください。

# 引数

  * `file::String`: 気象ファイルへのパス
  * `args...`: テーブルを変換するための引数のリスト。上記で可能な形式を参照してください。
  * `date_format = DateFormat("yyyy-mm-ddTHH:MM:SS.s")`: `DateTime`列のフォーマット
  * `hour_format = DateFormat("HH:MM:SS")`: `Time`列のフォーマット（例：`hour_start`）
  * `duration`: ファイルに存在する場合、`duration`列を解析するための関数。通常は`Dates.Day`または`Dates.Minute`です。

列が存在しない場合、`hour_format`と`hour_start`および`hour_end`列、さらに`date`列を使用して期間が計算されます。

# 例

```julia
using PlantMeteo, Dates

file = joinpath(dirname(dirname(pathof(PlantMeteo))),"test","data","meteo.csv")

meteo = read_weather(
    file,
    :temperature => :T,
    :relativeHumidity => (x -> x ./100) => :Rh,
    :wind => :Wind,
    :atmosphereCO2_ppm => :Cₐ,
    date_format = DateFormat("yyyy/mm/dd")
)
```
