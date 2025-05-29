```
hardware_transform_Ω(Ω,device_capabilities::DeviceCapabilities=get_device_capabilities())
```

Given the `device_capabilities` of the machine and a Rabi frequency (Ω) [`Waveform`](@ref), return a transformed Ω capable of being implemented by the machine along with the error between the original ($A$) and transformed ($B$) waveforms calculated as $\Vert A - B\Vert_1$. If the waveform durations are different, the shorter waveform is padded with zeros for values to make the durations equal in error calculation.

# Logs/Warnings/Exceptions

Exceptions are thrown if Ω is:

  * Not of type [`BloqadWaveforms.Waveform`](@ref)
  * Not present (`nothing` was passed in)
  * Not a global drive (e.g.: Vector of Waveforms, localized Ω is not supported)
  * the maximum slope allowed for the waveform from `device_capabilities` is set to infinity
  * the minimum time step allowed for the waveform from `device_capabilities` is set to zero

Debug logs are issued if the following are encountered in Ω:

  * duration may be rounded due to time resolution from `device_capabilities`
  * the initial waveform does not start/end in zero for its value
  * the values in the waveform exceed `device_capabilities` supported values, and must be clipped

# Examples

```jldoctest; setup:=(using BloqadeWaveforms)
julia> wf = sinusoidal(duration=2, amplitude=1.3*π);

julia> hardware_transform_Ω(wf)
(Waveform(_, 2.0), 2.632451578170084)
```
