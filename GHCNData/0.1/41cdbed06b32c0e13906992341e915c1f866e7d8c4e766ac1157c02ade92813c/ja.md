```
select_data(
    time_interval::Tuple{Date, Date},
    lat_interval::Tuple{Real, Real},
    lon_interval::Tuple{Real, Real},
    element::String,
)
```

特定の地域と時間期間から、`element` タイプのすべてのデータをロードします。例えば、`TMAX`。利用可能な要素の詳細については、NOAAのREADMEのセクションIIIを参照してください[1]。

結果は...

例:

```julia
using Dates, GHCNData
lat_interval = (50, 60);
lon_interval = (-10, 2);
time_interval = (Date(2010), Date(2020));
element = "TMAX"
data = select_data(time_interval, lat_interval, lon_interval, element)
```

[1] - https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt
