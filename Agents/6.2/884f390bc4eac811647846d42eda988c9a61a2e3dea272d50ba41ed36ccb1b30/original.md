```
ABMObservable(model; adata, mdata, when) → abmobs
```

`abmobs` contains all information necessary to step an agent based model interactively, as well as collect data while stepping interactively. `ABMObservable` also returned by [`abmplot`](@ref).

Calling `Agents.step!(abmobs, t)` will step the model for `t` time and collect data as in [`Agents.run!`](@ref).

The fields `abmobs.model, abmobs.adf, abmobs.mdf` are *observables* that contain the [`AgentBasedModel`](@ref), and the agent and model dataframes with collected data. Data are collected as described in [`Agents.run!`](@ref) using the `adata, mdata, when` keywords. All three observables are updated on stepping (when it makes sense).

All plotting and interactivity should be defined by `lift`ing these observables.
