```
Results(m::AbstractModel, p::Inputs{MultiPhase}; digits=8)
```

return a `Results` struct with fieldnames:

```
voltage_magnitudes
real_power_injections
reactive_power_injections
current_magnitudes
real_sending_end_powers
reactive_sending_end_powers
```
