```
struct DCLine <: Modification
    
DCLine(;file)
```

この [`Modification`](@ref) は、モデルに追加する dc ラインを表すファイルを受け取ります。テーブルの情報については [`summarize_table(::Val{:dc_line})`](@ref) を参照してください。

これは、各 dc ラインに対して（各時点で）単一の変数を作成し、それを `t_bus_idx` の `pbal_bus` に追加し、`f_bus_idx` からは減算します。電圧角の要件を無視して、無損失の電力移転を表します。

# 実装されたインターフェース

  * [`modify_raw_data!(mod::DCLine, config, data)`](@ref) - `mod.file => data[:dc_line]` をロードします。
  * [`modify_model!(mod::DCLine, config, data, model)`](@ref) - `data[:dc_lines]` からモデルに dc ラインを追加し、`pflow_dc` 変数を作成し、対応する `pflow_bus` 変数に追加/減算します。
