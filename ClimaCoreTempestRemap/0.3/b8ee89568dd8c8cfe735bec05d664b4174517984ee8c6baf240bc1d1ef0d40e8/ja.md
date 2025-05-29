```
remap_weights(
    weightfile::AbstractString,
    meshfile_in::AbstractString,
    meshfile_out::AbstractString,
    meshfile_overlap::AbstractString;
    verbose=false,
    kwargs...
)
```

`meshfile_in` から `meshfile_out` へのリマッピング重みを含む SCRIP 形式のファイル `weightfile` を作成します。ここで、`meshfile_overlap` は [`overlap_mesh`](@ref) を介して構築されます。

キーワード引数はコマンドラインオプションとして渡されます。これには以下が含まれます：

  * `in_type` / `out_type`: 入力および出力メッシュのタイプ：

      * `"fv"` (デフォルト): 有限体積（要素ごとに1つの値）
      * `"cgll"`: 連続 GLL 有限要素法（同位置ノードの単一値）
      * `"dgll"`: 不連続 GLL 有限要素法（同位置ノードの重複値）
  * 'in*np'/'out*np': 入力および出力メッシュの次数
  * 'mono': リマッピングの単調性

単調リマッピングのために `mono = true` を設定します。情報を印刷するには `verbose=true` を設定します。

[Tempest remap: オフラインマップ生成](https://github.com/ClimateGlobalChange/tempestremap/#offline-map-generation) を参照してください。
