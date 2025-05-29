```
StartInvData <: AbstractInvData
```

Investment data in which the initial capacity is specified in the `AbstractInvData`. The structure is similiar to [`NoStartInvData`](@ref) with the addition of the field **`initial::TimeProfile`**, see below.

# Fields in addition to [`NoStartInvData`](@ref)

  * **`initial::TimeProfile`** is the initial capacity as `TimeProfile`. Retirement of the initial capacity can be achieved through a decreasing capacity.
