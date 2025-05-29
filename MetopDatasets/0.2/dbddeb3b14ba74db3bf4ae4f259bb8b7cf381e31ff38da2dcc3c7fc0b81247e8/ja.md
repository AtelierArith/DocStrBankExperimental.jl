```
MetopDataset(file_path::AbstractString; auto_convert::Bool = true, high_precision::Bool=false, maskingvalue = missing)
MetopDataset(file_pointer::IO; auto_convert::Bool = true, high_precision::Bool=false, maskingvalue = missing)
MetopDataset(f::Function, file_path::AbstractString; auto_convert::Bool = true, high_precision::Bool=false, maskingvalue = missing)
```

Metop Nativeバイナリファイルまたは`IO`からNativeバイナリファイルへのMetopDatasetをロードします。作成時にはメタデータのみがロードされ、すべての変数は遅延ロードされます。変数はファイル内のデータレコードの異なるフィールドに対応しています。属性にはファイル内のメイン製品ヘッダーからのすべての情報が含まれています。

`auto_convert=true`は、`VInteger`などのMetopDatasets特有の型を、`Float64`などの一般的なnetCDF準拠型に自動的に変換します。これは、単純なスケールファクターで表現できないスケーリングが必要な変数を自動的にスケールします。例えば、異なるバンドのスペクトルが異なるスケーリングファクターを持つIASIスペクトルなどです。

選択されたフィールドはメモリを節約するために`Float32`に変換されます。通常、`Float32`は計器の精度を表現するのに十分です。`high_precision=true`を設定すると、場合によってはこれらの変数が`Float64`に変換されます。

`maskingvalue = NaN`は`missing`値をNaNに置き換えます。これは通常は浮動小数点ですが、整数に対して問題を引き起こす可能性があります。詳細についてはドキュメントページを参照してください。

## 例

```julia-repl
julia> file_path = "test/testData/ASCA_SZR_1B_M03_20230329063300Z_20230329063558Z_N_C_20230329081417Z"
julia> ds = MetopDataset(file_path);
julia>
julia> # 変数のメタデータを表示
julia> ds["latitude"]
latitude (82 × 96)
  Datatype:    Union{Missing, Float64} (Int32)
  Dimensions:  xtrack × atrack
  Attributes:
   description          = Latitude (-90 to 90 deg)
   missing_value        = Int32[-2147483648]
   scale_factor         = 1.0e-6
julia>
julia> # 変数のサブセットをロード  
julia> lat_subset = ds["latitude"][1:2,1:3] # 緯度の小さなサブセットをロードします。
2×3 Matrix{Union{Missing,Float64}}:
    -33.7308  -33.8399  -33.949
    -33.7139  -33.823   -33.9322
julia>
julia> # 変数全体をロード  
julia> lat = ds["latitude"][:,:]
julia>
julia> # データセットを閉じる
julia> close(ds);
```
