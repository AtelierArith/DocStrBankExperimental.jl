```
AutoReverseDiff{compile}
```

Struct used to select the [ReverseDiff.jl](https://github.com/JuliaDiff/ReverseDiff.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoReverseDiff(; compile::Union{Val, Bool} = Val(false))
```

# Fields

  * `compile::Union{Val, Bool}`: whether to allow pre-recording and reusing a tape (which speeds up the differentiation process).

      * If `compile=false` or `compile=Val(false)`, a new tape must be recorded at every call to the differentiation operator.
      * If `compile=true` or `compile=Val(true)`, a tape can be pre-recorded on an example input and then reused at every differentiation call.

    The boolean version of this keyword argument is taken as the type parameter.

!!! warning
    Pre-recording a tape only captures the path taken by the differentiated function *when executed on the example input*. If said function has value-dependent branching behavior, reusing pre-recorded tapes can lead to incorrect results. In such situations, you should keep the default setting `compile=Val(false)`. For more details, please refer to ReverseDiff's [`AbstractTape` API documentation](https://juliadiff.org/ReverseDiff.jl/dev/api/#The-AbstractTape-API).


!!! info
    Despite what its name may suggest, the `compile` setting does not prescribe whether or not the tape is compiled with [`ReverseDiff.compile`](https://juliadiff.org/ReverseDiff.jl/dev/api/#ReverseDiff.compile) after being recorded. This is left as a private implementation detail.

