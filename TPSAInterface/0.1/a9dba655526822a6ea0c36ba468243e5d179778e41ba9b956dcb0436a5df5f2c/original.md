```
InitGTPSA{D,DD}
```

Struct used to define a TPSA using the [GTPSA.jl](https://github.com/bmad-sim/GTPSA.jl) backend.

Defined by [`TPSAInterface.jl`](https://github.com/bmad-sim/TPSAInterface.jl).

# Constructors

```
InitGTPSA{D,DD}(; dynamic_descriptor=nothing)
```

## Fields

  * For static `Descriptor` resolution:

      * `D` is the `Descriptor`
      * `DD` is `Nothing` and `dynamic_descriptor` is `nothing`
  * For dynamic `Descriptor` resolution:

      * `D == GTPSA.Dynamic`
      * `DD == Descriptor` and `dynamic_descriptor` is said `Descriptor`
