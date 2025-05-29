```
AveragedTimeInterval(interval; window=interval, stride=1)
```

Returns a `schedule` that specifies periodic time-averaging of output. The time `window` specifies the extent of the time-average, which reoccurs every `interval`.

`output` is computed and accumulated into the average every `stride` iterations during the averaging window. For example, `stride=1` computes output every iteration, whereas `stride=2` computes output every other iteration. Time-averages with longer `stride`s are faster to compute, but less accurate.

The time-average of $a$ is a left Riemann sum corresponding to

$$
⟨a⟩ = T⁻¹ \int_{tᵢ-T}^{tᵢ} a \mathrm{d} t \, ,
$$

where $⟨a⟩$ is the time-average of $a$, $T$ is the time-window for averaging, and the $tᵢ$ are discrete times separated by the time `interval`. The $tᵢ$ specify both the end of the averaging window and the time at which output is written.

# Example

```jldoctest averaged_time_interval
using Oceananigans.OutputWriters: AveragedTimeInterval
using Oceananigans.Utils: days

schedule = AveragedTimeInterval(4days, window=2days)

# output
AveragedTimeInterval(window=2 days, stride=1, interval=4 days)
```

An `AveragedTimeInterval` schedule directs an output writer to time-average its outputs before writing them to disk:

```@example averaged_time_interval
using Oceananigans
using Oceananigans.Units

model = NonhydrostaticModel(grid=RectilinearGrid(size=(1, 1, 1), extent=(1, 1, 1)))

simulation = Simulation(model, Δt=10minutes, stop_time=30days)

simulation.output_writers[:velocities] = JLD2Writer(model, model.velocities,
                                                    filename= "averaged_velocity_data.jld2",
                                                    schedule = AveragedTimeInterval(4days, window=2days, stride=2))
```
