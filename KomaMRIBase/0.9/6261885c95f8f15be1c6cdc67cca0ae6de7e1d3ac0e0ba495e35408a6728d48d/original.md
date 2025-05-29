```
adc = ADC(N, T)
adc = ADC(N, T, delay)
adc = ADC(N, T, delay, Δf, ϕ)
```

The ADC struct represents the Analog to Digital Converter (ADC) of a sequence event.

# Arguments

  * `N`: (`::Int64`) number of acquired samples
  * `T`: (`::Float64`, [`s`]) duration to acquire the samples
  * `delay`: (`::Float64`, [`s`]) delay time to start the acquisition
  * `Δf`: (`::Float64`, [`Hz`]) delta frequency. It is meant to compensate RF pulse phases
  * `ϕ`: (`::Float64`, `[rad]`) phase. It is meant to compensate RF pulse phases

# Returns

  * `adc`: (`::ADC`) ADC struct

# Examples

```julia-repl
julia> adc = ADC(16, 1, 0.1)

julia> seq = Sequence(); seq += adc; plot_seq(seq)
```
