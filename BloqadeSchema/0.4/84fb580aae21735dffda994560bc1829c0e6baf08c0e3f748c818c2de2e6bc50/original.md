```
hardware_transform_Δ(Δ,device_capabilities::DeviceCapabilities=get_device_capabilities())
```

Given the `device_capabilities` of the machine and a detuning waveform Δ, return a transformed Δ capable of being implemented by the machine along with the error between the original ($A$) and transformed ($B$) waveforms calculated as $\Vert A - B\Vert_1$. If the waveform durations are different, the shorter waveform is padded with zeros for values to make the durations equal in error calculation.

# Logs/Warnings/Exceptions

Exceptions are thrown if Δ is:

  * Not of type [`BloqadWaveforms.Waveform`](@ref)
  * Not present (`nothing` was passed in)
  * Not a global drive (e.g. Vector of Waveforms, localized Δ is not supported)
  * the maximum slope allowed for the waveform from `device_capabilities` is set to infinity
  * the minimum time step allowed for the waveform from `device_capabilities` is set to zero

Debug logs are issued if the following are encountered in Δ:

  * duration may be rounded due to time resolution from `device_capabilities`
  * the initial waveform does not start/end in zero for its value
  * the values in the waveform exceed `device_capabilities` supported values, and must be clipped

# Examples

```jldoctest; setup:=(using BloqadeWaveforms)
julia> wf = sinusoidal(duration=2, amplitude=1.3*π);

julia> hardware_transform_Δ(wf)
(Waveform(_, 2.0), 0.06492452289703464)
```
