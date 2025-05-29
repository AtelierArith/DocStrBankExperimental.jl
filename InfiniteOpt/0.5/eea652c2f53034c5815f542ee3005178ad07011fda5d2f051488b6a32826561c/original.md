```
parameter_refs(mref::MeasureRef)::Tuple
```

Return the tuple of infinite parameters that the measured expression associated `mref` depends on once the measure has been evaluated. Note that this will correspond to the parameter dependencies of the measure function excluding those included in the measure data.

**Example**

```julia-repl
julia> parameter_refs(meas)
(t,)
```
