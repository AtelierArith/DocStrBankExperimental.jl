```
run_e4st(config) -> out_path

run_e4st(filename(s)) -> out_path
```

E4STを実行するためのトップレベル関数です。ここでは、何が起こるかの一般的な概要を示します。

1. ブックキーピング

      * [`read_config(config_file)`](@ref) - 直接渡されていない場合、ファイルから`config`を読み込みます。
      * [`save_config(config)`](@ref) - `config`は`config[:out_path]`に保存されます。
      * [`start_logging!(config)`](@ref) - ロギングが開始され、基本的な情報が[`log_start`](@ref)を介してログに記録されます。
2. 入力データの読み込み

      * [`read_data(config)`](@ref) - `config`で指定されたファイルからデータが読み込まれます。
3. JuMPモデルの構築と最適化

      * [`setup_model(config, data)`](@ref) - `model`（JuMPモデル）が設定されます。
      * [`JuMP.optimize!(model)`](https://jump.dev/JuMP.jl/stable/reference/solutions/#JuMP.optimize!) - `model`が最適化されます。
4. 結果の処理

      * [`parse_results!(config, data, model)`](@ref) - `model`から必要なすべての値とシャドウプライスを取得し、data[:results][:raw]に保存します（[`get_raw_results`](@ref)および[`get_results`](@ref）を参照）し、`config[:save_data_parsed]`が`true`の場合（デフォルトは`true`）に`data`を保存します。これは、結果処理が完了する前にエラーが発生した場合に備えて主に保存されます。これにより、モデルを再実行する必要がなくなります。
      * [`process_results!(config, data)`](@ref) - `config`内の各`mod`に対して[`modify_results!(mod, config, data)`](@ref)を呼び出します。`config[:save_data_processeded]`が`true`の場合（デフォルトは`true`）に`data`を保存します。
5. 必要に応じて、さらにシミュレーションを実行します。

      * 詳細については、[`Iterable`](@ref)および[`read_config`](@ref)を参照してください。
