```julia
struct Solution{T, P, C, S}
```

シミュレーションの解であり、`run_simulation`によって返されます。これらは、[Postprocessing](@ref)で説明されている任意の後処理関数に渡すことができるか、特定の値を抽出するためにインデックスを付けることができます。

# インデックス付け

解をインデックス付けする方法はいくつかあります。まず、整数で`Solution`をインデックス付けすることによって、単一のフレームを含む解を抽出できます。

```jldoctest; setup = :(using HallThruster: HallThruster as het; config = het.Config(discharge_voltage = 300, thruster = het.SPT_100, anode_mass_flow_rate=5e-6, domain = (0.0, 0.08)); simparams = het.SimParams(dt = 5e-9, grid = het.EvenGrid(50), duration = 1e-3, num_save = 101, verbose=false); solution = het.run_simulation(config, simparams))
julia> solution = het.run_simulation(config, simparams)
Hall thruster solution with 101 saved frames (retcode: success, end time: 0.001 seconds)

julia> solution[51]
Hall thruster solution with 1 saved frame (retcode: success, end time: 0.0005 seconds)
```

次に、ベクトルまたはベクトルのようなオブジェクトで解をインデックス付けして、フレームの範囲を抽出できます。

```jldoctest; setup = :(using HallThruster: HallThruster as het; config = het.Config(discharge_voltage = 300, thruster = het.SPT_100, anode_mass_flow_rate=5e-6, domain = (0.0, 0.08)); simparams = het.SimParams(dt = 5e-9, grid = het.EvenGrid(50), duration = 1e-3, num_save = 101, verbose=false); solution = het.run_simulation(config, simparams))
julia> solution[51:end] # get last 51 frames
Hall thruster solution with 51 saved frames (retcode: success, end time: 0.001 seconds)

julia> solution[begin:2:end] # get every other frame
Hall thruster solution with 51 saved frames (retcode: success, end time: 0.001 seconds)

julia> solution[[1, 51, 101]] # get only frames 1, 51, 101
Hall thruster solution with 3 saved frames (retcode: success, end time: 0.001 seconds)
```

最後に、シンボルまたは[Symbol, Integer]でインデックス付けして、その解のすべてのフレームのプラズマデータを取得できます。

```julia
solution[:ni, 1] 	# get ion density of first charge state for all frames
solution[:ui] 		# get ion velocity for all charge states and frames

# These return the same thing
solution[:∇pe]
solution[:grad_pe]
```

インデックス付けに使用できる有効なフィールドのリストを取得するには、`HallThruster.valid_fields()`を呼び出します。特殊文字を含むフィールドの代替名のリストを取得するには、`HallThruster.alternate_field_names()`を呼び出します。

`Base.getindex(sol::Solution, field::Symbol)`および`Base.getindex(sol::Solution, field::Symbol, charge::Integer)`の詳細については、ドキュメントを参照してください。

# フィールド

  * `t::Any`: シミュレーション出力が保存された時刻（秒単位）のベクトル
  * `frames::Any`: `t`で指定された時刻におけるシミュレーション状態のフレームまたはスナップショットのベクトル
  * `params::Any`: 解のパラメータベクトル。シミュレーションに関する補助情報を含みます。
  * `config::Any`: シミュレーションを実行するために使用された`Config`
  * `retcode::Symbol`: 解の戻りコード。これは3つの値のいずれかです：

    1. `:success`: シミュレーションが正常に完了しました。
    2. `:failure`: 数値的な問題や不安定性によりシミュレーションが失敗し、解のどこかで`NaN`または`Inf`が検出されました。
    3. `:error`: 別のエラーが発生しました。どのようなエラーが発生したかを確認するには、`error`文字列をチェックしてください。
  * `error::String`: エラーが発生した場合のエラーテキストとバックトレースを保持します。`sol.retcode != :error`の場合は空です。
