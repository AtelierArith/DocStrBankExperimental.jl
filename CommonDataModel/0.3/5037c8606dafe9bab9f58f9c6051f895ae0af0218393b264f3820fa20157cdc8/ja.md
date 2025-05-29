```
vsubset = CommonDataModel.@select(v,expression)
dssubset = CommonDataModel.@select(ds,expression)
```

変数 `v`（またはデータセット `ds`）の条件 `expression` を満たすサブセットをビューとして返します。条件は次の形式を持ちます：

`condition₁ && condition₂ && condition₃ ... conditionₙ`

すべての条件は単一の1D変数（通常は座標変数、以下では `coord` と呼ばれます）を含む必要があります。`v` が変数である場合、関連する1D変数は変数 `v` と共有の次元を持つ必要があります。すべてのローカル変数には `$` プレフィックスが必要です（以下の例を参照）。このマクロは実験的であり、変更される可能性があります。

すべての条件は次のいずれかを実行できます：

  * 最近接一致： `coord ≈ target_coord` （`≈` タイプ `\approx` の後にTABキーを押します）。`target_coord` に最も近いインデックスに対応するデータのみが読み込まれます。
  * 許容範囲を持つ最近接一致： `coord ≈ target_coord ± tolerance`。前述の通りですが、`coord` の最も近い値と `target_coord` の間の差が `tolerance` よりも大きい（絶対値で）場合、空の配列が返されます。
  * スカラー値に対して動作する条件。たとえば、`condition` が `10 <= lon <= 20` の場合、経度が10から20の間のすべてのデータを読み込みます。または `abs(lat) > 60` は、60° N および 60° S の北にあるすべての変数を読み込みます（`lon` と `lat` の1D変数が経度と緯度のために存在することを前提としています）。

すべての条件を満たすデータのみが読み込まれます。すべての条件は `&&`（論理積）で連結する必要があります。追加の括弧や `||`（論理和）などの他の論理演算子を含めてはいけません。

ビューを通常の配列に変換するには、`collect`、`Array`、または通常のインデックスを使用できます。juliaのように、スカラーのビューはゼロ次元の配列にラップされ、`[]` を使用して参照解除できます。ビューを変更すると、基になるファイルが変更されます（ファイルが書き込み可能として開かれている場合、そうでない場合はエラーが発生します）。

任意のビューについて、`parentindices(vsubset)` を使用して選択クエリに一致するインデックスを取得できます。

## 例

ランダムデータを持つサンプルファイルを作成します：

```julia
using NCDatasets, Dates
using CommonDataModel: @select
# または
# using NCDatasets: @select

fname = "sample_file.nc"
lon = -180:180
lat = -90:90
time = DateTime(2000,1,1):Day(1):DateTime(2000,1,3)
SST = randn(length(lon),length(lat),length(time))

ds = NCDataset(fname,"c")
defVar(ds,"lon",lon,("lon",));
defVar(ds,"lat",lat,("lat",));
defVar(ds,"time",time,("time",));
defVar(ds,"SST",SST,("lon","lat","time"));


# バウンディングボックスで読み込む
v = @select(ds["SST"],30 <= lon <= 60 && 40 <= lat <= 80)

# 条件内でローカル変数を $ を使って置き換える
lonr = (30,60) # 経度範囲
latr = (40,80) # 緯度範囲

v = @select(ds["SST"],$lonr[1] <= lon <= $lonr[2] && $latr[1] <= lat <= $latr[2])

# `IntervalSets.jl` の `ClosedInterval` に基づいて選択することもできます。
# 30..60 と 60 ± 20 の両方が `ClosedInterval` を構築します。詳細については、ドキュメントを参照してください。

lon_interval = 30..60
lat_interval = 60 ± 20
v = @select(ds["SST"], lon ∈ $lon_interval && lat ∈ $lat_interval)

# 選択クエリに一致するインデックスを取得
(lon_indices,lat_indices,time_indices) = parentindices(v)

# 選択クエリに一致する経度を取得
v_lon = v["lon"]

# 最も近い時間インスタンスを見つける
v = @select(ds["SST"],time ≈ DateTime(2000,1,4))

# 最も近い時間インスタンスを見つけるが、2時間よりも早くも遅くもない
# 時間インスタンスが存在しない場合は空の配列が返されます

v = @select(ds["SST"],time ≈ DateTime(2000,1,3,1) ± Hour(2))

close(ds)
```

同じ次元名を持つ任意の1D変数を `@select` で使用できます。たとえば、温度と塩分の時系列がある場合、温度値は塩分に基づいて選択することもできます：

```julia
using NCDatasets, Dates
using CommonDataModel: @select
fname = "sample_series.nc"
# サンプルの時系列を作成
time = DateTime(2000,1,1):Day(1):DateTime(2009,12,31)
salinity = randn(length(time)) .+ 35
temperature = randn(length(time))

NCDataset(fname,"c") do ds
    defVar(ds,"time",time,("time",));
    defVar(ds,"salinity",salinity,("time",));
    defVar(ds,"temperature",temperature,("time",));
end

ds = NCDataset(fname)

# 塩分が35より大きい1月のすべての温度データを読み込む
v = @select(ds["temperature"],Dates.month(time) == 1 && salinity >= 35)

# これは次のように等価です：
v2 = ds["temperature"][findall(Dates.month.(time) .== 1 .&& salinity .>= 35)]

v == v2
# true を返します
close(ds)
```

!!! note
    最適なパフォーマンスを得るために、特にHTTP/OPeNDAP経由でデータを読み込む際には、連続したデータ範囲を読み込むように努めるべきです。

