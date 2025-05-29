```
PostprocessCallback(; interval::Integer=0, dt=0.0, exclude_boundary=true, filename="values",
                    output_directory="out", append_timestamp=false, write_csv=true,
                    write_json=true, write_file_interval=1, funcs...)
```

シミュレーションデータを定期的に後処理するためのコールバックを作成します。このコールバックは、シミュレーション中の指定された間隔でユーザー定義の関数 `func` を実行することを可能にします。この関数はシミュレーションの現在の状態に適用され、その結果は保存するか、さらなる分析に使用できます。提供された関数は匿名であってはならず、関数名は値の名前の一部として使用されます。

コールバックは、固定の時間ステップ数（`interval`）または固定のシミュレーション時間の間隔（`dt`）によってトリガーされます。

# キーワード

  * `funcs...`:   シミュレーション中の指定された間隔で実行される関数。               各関数は `(system, data, t)` という引数を持っている必要があり、               これはすべてのシステムに対して呼び出されます。ここで `data` は               システムタイプに依存するフィールドを持つ名前付きタプルであり、`t` は               現在のシミュレーション時間です。各システムの利用可能なデータは               `available_data(system)` で確認できます。               ここで使用できる事前定義されたカスタム量のリストについては、               [Custom Quantities](@ref custom_quantities) を参照してください。
  * `interval=0`: コールバックの各呼び出しの間の時間ステップ数を指定します。               `0` に設定すると、コールバックは時間ステップに基づいてトリガーされません。               `interval` または `dt` のいずれかは 0 より大きい値に設定する必要があります。
  * `dt=0.0`: コールバックの各呼び出しの間のシミュレーション時間の間隔を指定します。           `0.0` に設定すると、コールバックはシミュレーション時間に基づいてトリガーされません。           `interval` または `dt` のいずれかは 0 より大きい値に設定する必要があります。
  * `exclude_boundary=true`: `true` に設定すると、境界粒子は後処理から除外されます。
  * `filename="values"`: 保存される後処理ファイルのファイル名。
  * `output_directory="out"`: 後処理の結果が保存されるパス。
  * `write_csv=true`: `true` に設定すると、csvファイルを書き込みます。
  * `write_json=true`: `true` に設定すると、jsonファイルを書き込みます。
  * `append_timestep=false`: `true` に設定すると、現在のタイムスタンプがファイル名に追加されます。
  * `write_file_interval=1`: ファイルは、各 `write_file_interval` 回の後処理実行ステップの後に書き込まれます。値が 0 の場合、ファイルはシミュレーションの終了時にのみ書き込まれ、I/O オーバーヘッドが排除されます。

# 例

```jldoctest; output = false
# 100 時間ステップごとにトリガーされるコールバックを作成
postprocess_callback = PostprocessCallback(interval=100, example_quantity=kinetic_energy)

# 0.1 シミュレーション時間単位ごとにトリガーされるコールバックを作成
postprocess_callback = PostprocessCallback(dt=0.1, example_quantity=kinetic_energy)

# 出力
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PostprocessCallback                                                                              │
│ ═══════════════════                                                                              │
│ dt: ……………………………………………………………………… 0.1                                                              │
│ write file: ………………………………………………… always                                                           │
│ exclude boundary: ………………………………… yes                                                              │
│ filename: ……………………………………………………… values                                                           │
│ output directory: ………………………………… out                                                              │
│ append timestamp: ………………………………… no                                                               │
│ write json file: …………………………………… yes                                                              │
│ write csv file: ……………………………………… yes                                                              │
│ function1: …………………………………………………… example_quantity                                                 │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
