```
SolutionSavingCallback(; interval::Integer=0, dt=0.0, save_times=Array{Float64, 1}([]),
                       save_initial_solution=true, save_final_solution=true,
                       output_directory="out", append_timestamp=false, prefix="",
                       verbose=false, write_meta_data=true, max_coordinates=2^15,
                       custom_quantities...)
```

定期的に現在の数値解をVTK形式で保存するためのコールバック。`interval`を渡して`interval`時間ステップごとに保存するか、`dt`を渡して統合時間の`dt`の間隔で保存するために追加の`tstops`を加えます（これにより解が変わる可能性があります）。

追加のユーザー定義量は、`(v, u, t, system)`を`Array`にマッピングする関数をキーワード引数として渡すことで保存できます。列は`u`と同じ順序で粒子を表します。特定のシステムに対してカスタム量を無視するには、`nothing`を返します。

# キーワード

  * `interval=0`:                 解を`interval`時間ステップごとに保存します。
  * `dt`:                         統合時間の`dt`の定期的な間隔で解を保存します                               追加の`tstops`を加えることによって（これにより解が変わる可能性があります）。
  * `save_times=[]`               解を保存する時間のリスト。
  * `save_initial_solution=true`: 初期解を保存します。
  * `save_final_solution=true`:   最終解を保存します。
  * `output_directory="out"`:     VTKファイルを保存するディレクトリ。
  * `append_timestamp=false`:     現在のタイムスタンプを出力ディレクトリに追加します。
  * 'prefix=""':                  ファイル名に追加されるプレフィックス。
  * `custom_quantities...`:       追加のユーザー定義量。
  * `write_meta_data=true`:       メタデータを書き込みます。
  * `verbose=false`:              ファイルが書き込まれたときに標準IOに出力します。
  * `max_coordinates=2^15`:       粒子の座標は、その絶対値がこの閾値を超えるとクリップされます。
  * `custom_quantities...`:   VTK出力に含める追加のカスタム量。                           各カスタム量は`(system, data, t)`の関数でなければならず、                           これはすべてのシステムに対して呼び出されます。                           `data`はシステムタイプに依存するフィールドを持つ名前付きタプルで、                           `t`は現在のシミュレーション時間です。                           各システムの利用可能なデータは`available_data(system)`で確認できます。                           ここで使用できる事前定義されたカスタム量のリストについては、                           [Custom Quantities](@ref custom_quantities)を参照してください。

# 例

```jldoctest; output = false, filter = [r"output directory:.*", r"\s+│"]
# 100時間ステップごとに保存
saving_callback = SolutionSavingCallback(interval=100)

# シミュレーション時間の0.1の間隔で保存
saving_callback = SolutionSavingCallback(dt=0.1)

# 各システムの運動エネルギーを「my_custom_quantity」として追加で保存
saving_callback = SolutionSavingCallback(dt=0.1, my_custom_quantity=kinetic_energy)

# 出力
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ SolutionSavingCallback                                                                           │
│ ══════════════════════                                                                           │
│ dt: ……………………………………………………………………… 0.1                                                              │
│ custom quantities: ……………………………… [:my_custom_quantity => TrixiParticles.kinetic_energy]           │
│ save initial solution: …………………… yes                                                              │
│ save final solution: ………………………… yes                                                              │
│ output directory: ………………………………… *path ignored with filter regex above*                           │
│ prefix: ……………………………………………………………                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
