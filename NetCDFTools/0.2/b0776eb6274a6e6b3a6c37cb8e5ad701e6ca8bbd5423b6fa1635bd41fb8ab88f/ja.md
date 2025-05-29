```julia
nc_read(file; ...) -> Any
nc_read(
    file,
    band;
    type,
    period,
    ind,
    raw,
    nodata,
    verbose
) -> Any

```

# 引数

  * `band`  : 文字列（変数名）または整数（バンドID）。`int`が提供された場合、`bandName = nc_bands(file)[band]`
  * `type`  : 戻り値のデータ型、例：`Float32`
  * `period`: `[year_start, year_end]` または `year`、時間は3次元目にある必要があります。
  * `ind`   : `ind`が提供された場合、`period`は無視されます。
  * `raw`   : ブール値。

      * `true`: 生データ。
      * `false`（デフォルト）: `missing`は`nodata`に置き換えられます。
  * `verbose`: ブール値。`true`の場合、`data`と`ind`がコンソールに出力されます。
