```
TPS{D}([number]) where {D}
TPS{T,D}([number]) where {T<:Union{Float64,ComplexF64}}

TPS([number] [, use=(descriptor|tps)])
TPS{T}([number] [, use=(descriptor|tps)]) where {T<:Union{Float64,ComplexF64}}
TPS{T,GTPSA.Dynamic}([number] [, use=(descriptor|tps)]) where {T<:Union{Float64,ComplexF64}}
```

Constructor to create a new `TPS`, equal to `number` if provided. 

A constructed `TPS` must correspond to some previously defined `Descriptor`. As such, two "modes" of the `TPS` type may be  constructed to determine how the `Descriptor` to use is resolved:

1. Dynamic `Descriptor` resolution – The `Descriptor` is inferred at runtime, based on the passed arguments:

| Ctor Call                                | Descriptor                                                      |
|:---------------------------------------- |:--------------------------------------------------------------- |
| `TPS()`                                  | `GTPSA.desc_current`                                            |
| `TPS(use=descriptor)`                    | `descriptor`                                                    |
| `TPS(use=tps1)`                          | That of `tps1`                                                  |
| `TPS(tps)`                               | That of `tps`                                                   |
| `TPS(number)`                            | `GTPSA.desc_current`                                            |
| `TPS(number, use=(descriptor or tps1) )` | `descriptor` or that of `tps1`                                  |
| `TPS(tps, use=(descriptor or tps1) )`    | `descriptor` or that of `tps1` (copies + changes `Descriptor`!) |

The same applies for all of the above constructor calls with the constructors `TPS64(...)` and `ComplexTPS64(...)`. The created type will be a `TPS{T,GTPSA.Dynamic} where {T<:Union{Float64,ComplexF64}}`. Dynamic `Descriptor` resolution  will always be type stable, as the `Descriptor` for each `TPS` is not stored in the type definition. E.g., one can have  an array with elements of the concrete type `TPS{T,GTPSA.Dynamic}` even though the individual `TPS`s in the array may  have differing `Descriptor`s. Another example is typing the field of a struct as `TPS{T,GTPSA.Dynamic}`, so that field  can contain `TPS`s of different `Descriptor`s in a type-stable fashion. However, with dynamic `Descriptor` resolution  the `use` kwarg must be specified if the `Descriptor` is both not inferrable nor `GTPSA.desc_current` is the desired  `Descriptor`. For calls such as `zeros(TPS64, N)` or `TPS64(5.0)`, only `GTPSA.desc_current` can be inferred.

2. Static `Descriptor` resolution – The `Descriptor` is stored explicitly in the `TPS` type:

| Ctor Call                                | Descriptor                                     |
|:---------------------------------------- |:---------------------------------------------- |
| `TPS{descriptor}([number])`              | `descriptor`                                   |
| `TPS{descriptor2}(::TPS{T,descriptor1})` | `descriptor2` (copies + changes `Descriptor`!) |
| `TPS(::TPS{T,descriptor})`               | `descriptor`                                   |

The same applies for all of the above constructor calls with the constructors `TPS64{...}(...)` and `ComplexTPS64{...}(...)`. The created type will be a `TPS{T,descriptor} where {T<:Union{Float64,ComplexF64}}`. Care must be taken with static  `Descriptor` resolution to ensure type-stability, and in some cases it may not be possible. However, static resolution has  the benefit that the `Descriptor` is stored explicitly in the type. As such, `GTPSA.desc_current` is never used with this mode,  nor is the `use` kwarg. Calls such as `zeros(TPS64{descriptor}, N)` can be made ensuring the `Descriptor` of the output is correct.
