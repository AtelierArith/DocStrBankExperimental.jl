```
JLD2Writer(model, outputs; filename, schedule,
           dir = ".",
           indices = (:, :, :),
           with_halos = true,
           array_type = Array{Float32},
           file_splitting = NoFileSplitting(),
           overwrite_existing = false,
           init = noinit,
           including = [:grid, :coriolis, :buoyancy, :closure],
           verbose = false,
           part = 1,
           jld2_kw = Dict{Symbol, Any}())
```

Oceananigans `model` のための `JLD2Writer` を構築し、`outputs` にある `label, output` ペアを JLD2 ファイルに書き込みます。

引数 `outputs` は `Dict` または `NamedTuple` である可能性があります。`outputs` のキーは出力データを「名前付け」するシンボルまたは文字列です。`outputs` の値は、`output(model)` というシグネチャで呼び出される `AbstractField` か、`AbstractFields` の `WindowedTimeAverage`、関数、または呼び出し可能なオブジェクトです。

# キーワード引数

## ファイル名

  * `filename` (必須): 説明的なファイル名。`filename` が `".jld2"` で終わらない場合、ファイルパスに `".jld2"` が追加されます。
  * `dir`: 出力を保存するディレクトリ。デフォルト: `"."` (現在の作業ディレクトリ)。

## 出力頻度と時間平均

  * `schedule` (必須): 出力が保存されるタイミングを決定する `AbstractSchedule`。

## 出力前のスライスと型変換

  * `indices`: ディスクに書き込むインデックスを `Tuple` の `Colon`、`UnitRange`、または `Int` 要素で指定します。インデックスは `Colon`、`Int`、または連続した `UnitRange` でなければなりません。デフォルトは `(:, :, :)` または「すべてのインデックス」です。`!with_halos` の場合、インデックスからハロ領域が削除されます。例えば、`indices = (:, :, 1)` は最下層インデックスの xy スライスを保存します。
  * `with_halos` (Bool): 出力を書く前にフィールドからハロ領域を切り取るか保持するか。ハロ領域データを保持することは、後処理に役立つ場合があります。デフォルト: true。
  * `array_type`: 出力配列が保存前に変換される配列の型。デフォルト: `Array{Float32}`。

## ファイル管理

  * `file_splitting`: 出力ファイルを分割するスケジュール。新しいファイルには `_part1`、`_part2` などのサフィックスが付加されます。例えば、`file_splitting = FileSizeLimit(sz)` は出力ファイルのサイズが `sz` を超えたときに分割します。別の例は `file_splitting = TimeInterval(30days)` で、シミュレーション時間の30日ごとにファイルを分割します。デフォルトは分割なし (`NoFileSplitting()`) です。
  * `overwrite_existing`: ファイル名が衝突した場合に既存のファイルを削除します。デフォルト: `false`。

## 出力ファイルメタデータ管理

  * `init`: JLD2 出力ファイルが初期化されるときに実行される `init(file, model)` 形式の関数。デフォルト: `noinit(args...) = nothing`。
  * `including`: すべてのファイルに保存するモデルプロパティのリスト。デフォルト: `[:grid, :coriolis, :buoyancy, :closure]`

## その他のキーワード

  * `verbose`: 出力ライターが何をしているか、計算/書き込み時間やファイルサイズの統計をログに記録します。デフォルト: `false`。
  * `part`: ファイル分割時に使用される開始部分番号。デフォルト: 1。
  * `jld2_kw`: データが書き込まれるときに `jldopen` に渡されるキーワード引数の辞書。

# 例

$$
u
$$

、$v$、$w$ の 3D フィールドとトレーサー $c$ を、水平平均とともに出力します。

```@example
using Oceananigans
using Oceananigans.Utils: hour, minute

model = NonhydrostaticModel(grid=RectilinearGrid(size=(1, 1, 1), extent=(1, 1, 1)), tracers=:c)
simulation = Simulation(model, Δt=12, stop_time=1hour)

function init_save_some_metadata!(file, model)
    file["author"] = "Chim Riggles"
    file["parameters/coriolis_parameter"] = 1e-4
    file["parameters/density"] = 1027
    return nothing
end

c_avg =  Field(Average(model.tracers.c, dims=(1, 2)))

# 注意: model.velocities は NamedTuple です
simulation.output_writers[:velocities] = JLD2Writer(model, model.velocities,
                                                    filename = "some_data.jld2",
                                                    schedule = TimeInterval(20minute),
                                                    init = init_save_some_metadata!)
```

シミュレーション時間の 20 分ごとにトレーサー $c$ の時間平均および水平平均を `some_averaged_data.jld2` というファイルに出力します。

```@example
simulation.output_writers[:avg_c] = JLD2Writer(model, (; c=c_avg),
                                               filename = "some_averaged_data.jld2",
                                               schedule = AveragedTimeInterval(20minute, window=5minute))
```
