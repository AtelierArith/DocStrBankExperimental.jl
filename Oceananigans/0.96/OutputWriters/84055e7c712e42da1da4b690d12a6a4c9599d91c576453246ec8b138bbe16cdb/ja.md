```
AveragedTimeInterval(interval; window=interval, stride=1)
```

出力の周期的な時間平均を指定する `schedule` を返します。時間 `window` は、`interval` ごとに再発生する時間平均の範囲を指定します。

`output` は、平均化ウィンドウの間に `stride` 回の反復ごとに計算され、平均に蓄積されます。たとえば、`stride=1` は毎回の反復で出力を計算し、`stride=2` は毎回の反復の間隔で出力を計算します。より長い `stride` の時間平均は計算が速くなりますが、精度は低くなります。

$$
a
$$

の時間平均は、次の左リーマン和に対応します。

$$
⟨a⟩ = T⁻¹ \int_{tᵢ-T}^{tᵢ} a \mathrm{d} t \, ,
$$

ここで、$⟨a⟩$ は $a$ の時間平均、$T$ は平均化のための時間ウィンドウ、$tᵢ$ は時間 `interval` で区切られた離散的な時間です。$tᵢ$ は平均化ウィンドウの終わりと出力が書き込まれる時間の両方を指定します。

# 例

```jldoctest averaged_time_interval
using Oceananigans.OutputWriters: AveragedTimeInterval
using Oceananigans.Utils: days

schedule = AveragedTimeInterval(4days, window=2days)

# output
AveragedTimeInterval(window=2 days, stride=1, interval=4 days)
```

`AveragedTimeInterval` スケジュールは、出力ライターに出力をディスクに書き込む前に時間平均を取るよう指示します：

```@example averaged_time_interval
using Oceananigans
using Oceananigans.Units

model = NonhydrostaticModel(grid=RectilinearGrid(size=(1, 1, 1), extent=(1, 1, 1)))

simulation = Simulation(model, Δt=10minutes, stop_time=30days)

simulation.output_writers[:velocities] = JLD2Writer(model, model.velocities,
                                                    filename= "averaged_velocity_data.jld2",
                                                    schedule = AveragedTimeInterval(4days, window=2days, stride=2))
```
