```
getraster(T::Type{CHELSA{Future{BioClimPlus}}}, [layer]; date) => String
```

CHELSA [`BioClimPlus`](@ref) データをダウンロードし、次のレイヤーから選択します: `[:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19, :hurs_max, :clt_max, :sfcWind_max, :vpd_max, :rsds_max, :pet_penman_max, :cmi_max, :hurs_min, :clt_min, :sfcWind_min, :vpd_min, :rsds_min, :pet_penman_min, :cmi_min, :hurs_mean, :clt_mean, :sfcWind_mean, :vpd_mean, :rsds_mean, :pet_penman_mean, :cmi_mean, :hurs_range, :clt_range, :sfcWind_range, :vpd_range, :rsds_range, :pet_penman_range, :cmi_range, :gdd0, :gddlgd0, :gdgfgd0, :ngd0, :gdd5, :gddlgd5, :gdgfgd5, :ngd5, :gdd10, :gddlgd10, :gdgfgd10, :ngd10, :fcf, :fgd, :lgd, :scd, :gsl, :gst, :gsp, :npp, :swb, :swe, :kg0, :kg1, :kg2, :kg3, :kg4, :kg5]`。

モデルの選択については、[`Future`](@ref) のドキュメントを参照してください。

レイヤー引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

## キーワード

  * `date`: `Date` または `DateTime` オブジェクト、ベクター、または開始/終了日の日付のタプル。CHELSA CMIP5 には2041-2060年と2061-2080年の2つのデータセットしかありません。CMIP6 には2011-2040年、2041-2070年、2071-2100年の期間のデータセットがあります。日付はこれらの範囲内である必要があります。

## 例
