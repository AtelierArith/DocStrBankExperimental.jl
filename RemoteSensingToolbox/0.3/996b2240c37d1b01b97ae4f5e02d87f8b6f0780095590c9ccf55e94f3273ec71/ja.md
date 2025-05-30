```
table(raster, [sink])
```

ラスタを `Tables.jl` に互換性のあるテーブルに変換します。

すべての `missingvals` を `missing` に置き換えます。

# パラメータ

  * `raster`: テーブルに読み込む `AbstractRaster` または `AbstractRasterStack`。
  * `sink`: `Tables.jl` マテリアライザー (デフォルト = `Tables.columntable`)。

# 例

```julia
julia> src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1/");

julia> rs = RasterStack(src, [:blue, :green, :red, :nir]);

julia> table(rs, DataFrame) |> dropmissing!
40540174×5 DataFrame
      Row │ geometry               B2      B3      B4      B5     
          │ Tuple…                 UInt16  UInt16  UInt16  UInt16 
──────────┼───────────────────────────────────────────────────────
        1 │ (544335.0, 5.84578e6)    8345    8798    8216   14454
        2 │ (544335.0, 5.84576e6)    8064    8707    8106   15583
        3 │ (544365.0, 5.84576e6)    8247    8858    8135   17552
    ⋮     │           ⋮              ⋮       ⋮       ⋮       ⋮
 40540172 │ (676365.0, 5.60968e6)    8863    9867   10164   16688
 40540173 │ (676395.0, 5.60968e6)    8823    9684   10050   16210
 40540174 │ (676425.0, 5.60968e6)    8934    9898   10324   16947
                                             40540168 行が省略されました
```
