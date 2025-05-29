```
ComponentAffect(f::Function, sym, psym)
```

Creates a callback condition for a [`ComponentCallback`].

  * `f`: The affect function. Must be a function of the form `f(u, p, [event_idx], ctx)` where `event_idx` is only available in [`VectorContinousComponentCallback`](@ref).

      * Arguments of `f`

          * `u`: The current (mutable) value of the selected `sym` states, provided as a [`SymbolicView`](@ref) object.
          * `p`: The current (mutalbe) value of the selected `psym` parameters.
          * `event_idx`: The current event index, i.e. which `out` element triggerd in case of [`VectorContinousComponentCallback`](@ref).
          * `ctx::NamedTuple` a named tuple with context variables.

              * `ctx.model`: a referenc to the ocmponent model
              * `ctx.vidx`/`ctx.eidx`: The index of the vertex/edge model.
              * `ctx.src`/`ctx.dst`: src and dst indices (only for edge models).
              * `ctx.integrator`: The integrator object. Use [`extract_nw`](@ref) to obtain the network.
              * `ctx.t=ctx.integrator.t`: The current simulation time.
  * `sym`: A vector or tuple of symbols, which represent **states** (**excluding** inputs, outputs, observed) of the component model. Determines, which states will be available thorugh parameter `u` in the callback condition function `f`.
  * `psym`: A vector or tuple of symbols, which represetn **parameters** of the component mode. Determines, which parameters will be available in the condition function `f`

# Example

Consider a component model with states `[:u1, :u2]`, inputs `[:i]`, outputs `[:o]` and parameters `[:p1, :p2]`.

```
ComponentAffect([:u1, :o], [:p1]) do u, p, ctx
    u[:u1] = 0 # change the state
    p[:p1] = 1 # change the parameter
    @info "Changed :u1 and :p1 on vertex $(ctx.vidx)" # access context
end
```
