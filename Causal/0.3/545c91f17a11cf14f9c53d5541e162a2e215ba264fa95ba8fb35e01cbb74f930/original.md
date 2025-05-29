```julia
mutable struct Writer{A, FL, var"356", var"357", var"358", Symbol, var"359", var"366", Int, var"367", var"368", var"369", var"370"} <: Causal.AbstractSink
```

Constructs a `Writer` whose input bus is `input`. `buflen` is the length of the internal buffer of `Writer`. If not nothing, `plugin` is used to processes the incomming data. `path` determines the path of the file of `Writer`.

# Fields

  * `action::Any`: Writer action to write data to file
  * `path::String`: File path of the writer
  * `file::Any`: File in which data is recorded
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `input::Any`
  * `buflen::Any`
  * `plugin::Any`
  * `timebuf::Any`
  * `databuf::Any`
  * `sinkcallback::Any`

!!! note
    The type of `file` of `Writer` is [`JLD2`](https://github.com/JuliaIO/JLD2.jl).


!!! warning
    When initialized, the `file` of `Writer` is closed. See [`open(writer::Writer)`](@ref) and [`close(writer::Writer)`](@ref).

