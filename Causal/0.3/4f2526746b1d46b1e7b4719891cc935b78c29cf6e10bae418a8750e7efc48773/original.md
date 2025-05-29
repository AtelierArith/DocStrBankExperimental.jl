```julia
struct Memory{D, IN, TB, DB, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractMemory
```

Constructs a 'Memory`with input bus`input`. A 'Memory` delays the values of `input` by an amount of `numdelay`.  `initial` determines the transient output from the `Memory`, that is, until the internal buffer of `Memory` is full,  the values from `initial` is returned.

# Fields

  * `delay::Any`: Delay in seconds
  * `initial::Any`: Inital value of memory
  * `numtaps::Int64`: Number of taps memory. The number of taps is length of internal(timebuf, databuf) buffers of memory
  * `timebuf::Any`: Time buffer of memory to record time instants
  * `databuf::Any`: Data buffer of memory to record input data values
  * `input::Any`: Input port
  * `output::Any`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# Example

```jldoctest
julia> Memory(delay=0.1)
Memory(delay:0.1, numtaps:5, input:Inport(numpins:1, eltype:Inpin{Float64}), output:Outport(numpins:1, eltype:Outpin{Float64}))

julia> Memory(delay=0.1, numtaps=5)
Memory(delay:0.1, numtaps:5, input:Inport(numpins:1, eltype:Inpin{Float64}), output:Outport(numpins:1, eltype:Outpin{Float64}))
```
