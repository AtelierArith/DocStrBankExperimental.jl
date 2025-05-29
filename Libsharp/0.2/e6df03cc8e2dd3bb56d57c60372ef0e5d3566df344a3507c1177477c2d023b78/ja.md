```
sharp_execute!(args...) where T <: AbstractFloat
```

libsharp2 SHTジョブを実行します。

スピン0のフィールドの場合、maps[1]はマップ要素を含む配列である必要があります。同様に、スピン2のフィールドの場合、maps[1]とmaps[2]は2つのスピン-2成分を含みます。almsも同様の形式で、alms[1]とalms[2]はスピン-2フィールドを記述する調和関数です。

単精度の場合は`flags=0`を指定し、倍精度の場合は`flags=SHARP_DP`を指定する必要があります。

# 引数

  * `jobtype::Integer`: libsharpジョブタイプ
  * `spin::Integer`: フィールドのスピン
  * `alms::Array{Array{Complex{T},1},1}`: alm配列
  * `maps::Array{Array{T,1},1}`: マップ配列
  * `geom_info::GeomInfo`: ピクセル化情報
  * `alm_info::AlmInfo`: 球面調和係数情報
  * `flags::Integer`: 追加フラグ
