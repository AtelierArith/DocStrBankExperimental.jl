```
StandardABM(MicrobeType, space, timestep; kwargs...)
```

Extension of the `Agents.StandardABM` method for microbe types. Implementation of `AgentBasedModel` where agents can be added and removed at any time. If agents removal is not required, it is recommended to use the keyword argument `container = Vector` for better performance. See `Agents.AgentBasedModel` for detailed information on the keyword arguments.

**Arguments**

  * `MicrobeType`: subtype of `AbstractMicrobe{D}`, with explicitly specified dimensionality `D`. A list of available options can be obtained by running `subtypes(AbstractMicrobe)`.
  * `space`: a `ContinuousSpace{D}` with *the same* dimensionality `D` as MicrobeType which specifies the spatial properties of the simulation domain.
  * `timestep`: the integration timestep of the simulation.

**Keywords**

  * `properties`: additional container of data to specify model-level properties. MicrobeAgents.jl includes a set of default properties (detailed at the end).
  * `scheduler = Schedulers.fastest`
  * `rng = Random.default_rng()`
  * `warn = true`

**Default `properties`**

When a model is created, a default set of properties is included in the model (`MicrobeAgents.default_ABM_properties`):

```
DEFAULT_ABM_PROPERTIES = Dict(
    :chemoattractant => GenericChemoattractant{D,Float64}()
    :affect! => chemotaxis!
)
```

By including these default properties, we make sure that all the chemotaxis models will work even without extra user intervention. All these properties can be overwritten by simply passing an equivalent key to the `properties` dictionary when creating the model.
