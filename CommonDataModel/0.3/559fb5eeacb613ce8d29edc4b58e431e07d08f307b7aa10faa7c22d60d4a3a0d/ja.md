```
v = getindex(ds::AbstractDataset, varname::SymbolOrString)
```

データセット `ds` から変数 `varname` を `CFVariable` として返します。変数がインデックスされるとき、次の CF 規約が遵守されます：

  * `_FillValue` または `missing_value`（リストである可能性があります）は `missing` として返されます。
  * `scale_factor` と `add_offset` が適用されます（出力 = `scale_factor` * `data_in_file` +  `add_offset`）
  * 時間変数（単位属性およびカレンダー属性によって認識される）は通常 `DateTime` オブジェクトとして返されます。`CFTime.DateTimeAllLeap`、`CFTime.DateTimeNoLeap` および `CF.TimeDateTime360Day` は、julia で使用される先行グレゴリオ暦に変換できず、そのまま返されることに注意してください。（これらの日付タイプに関する詳細は [`CFTime.jl`](https://github.com/JuliaGeo/CFTime.jl) を参照してください。）カレンダーが定義されているが CF 規約で指定されたものの中にない場合、ファイル内のデータは日付構造に変換されません。

`getindex(ds, varname)` の呼び出しは通常 `ds[varname]` として書かれます。

変数がセル境界を表す場合、関連する変数の属性 `calendar` と `units` が指定されていない場合に使用されます。例えば：

```
dimensions:
  time = UNLIMITED; // (5 currently)
  nv = 2;
variables:
  double time(time);
    time:long_name = "time";
    time:units = "hours since 1998-04-019 06:00:00";
    time:bounds = "time_bnds";
  double time_bnds(time,nv);
```

この場合、変数 `time_bnds` は、両方の変数が CF 規約に従った bounds 属性を通じて関連しているため、`time` の単位とカレンダーを使用します。

[`cfvariable(ds, varname)`](@ref) も参照してください。
