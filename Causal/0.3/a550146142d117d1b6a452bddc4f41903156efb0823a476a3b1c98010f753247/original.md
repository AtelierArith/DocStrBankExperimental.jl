Constructs a `SinewaveGenerator` with output of the form

$$
    x(t) = A sin(2 \pi f  (t - \tau) + \phi) + B
$$

where $A$ is `amplitude`, $f$ is `frequency`, $\tau$ is `delay` and $\phi$ is `phase` and $B$ is `offset`.

# Fields

  * `amplitude::Real`: Amplitude
  * `frequency::Real`: Frequency
  * `phase::Real`: Phase
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offset
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
