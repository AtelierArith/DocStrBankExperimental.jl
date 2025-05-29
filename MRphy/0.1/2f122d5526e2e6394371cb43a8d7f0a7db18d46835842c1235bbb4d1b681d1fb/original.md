A struct for typical MR pulses: `Pulse <: AbstractPulse`.

# Fields:

*Mutable*:

  * `rf::TypeND(RF0D, [1,2])` (nT,) or (nT, nCoils).
  * `gr::TypeND(GR0D, [2])` (nT, 3), where 3 accounts for x-y-z channels.
  * `dt::T0D` (1,), simulation temporal step size, i.e., dwell time.
  * `des::String`, an description of the pulse to be constructed.

# Usages:

```
Pulse(rf, gr; dt=(4e-6)u"s", des="generic pulse")
```

See also: [`AbstractPulse`](@ref).
