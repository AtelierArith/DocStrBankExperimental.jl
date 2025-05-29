```
periodsleep(model::SimModel, busywait=false) -> nothing
```

Sleep for `model.Ts` s minus the time elapsed since the last call to [`savetime!`](@ref).

It calls [`sleep`](@extref Julia Base.sleep) if `busywait` is `false`. Else, a simple  `while` loop implements busy-waiting. As a rule-of-thumb, busy-waiting should be used if  `model.Ts < 0.1` s, since the accuracy of `sleep` is around 1 ms. Can be used to implement simple soft real-time simulations, see the example below.

!!! warning
    The allocations in Julia are garbage-collected (GC) automatically. This can affect the  timing. In such cases, you can temporarily stop the GC with `GC.enable(false)`, and restart it at a convenient time e.g.: just before calling `periodsleep`.


# Examples

```jldoctest
julia> model = LinModel(tf(2, [0.3, 1]), 0.25);

julia> function sim_realtime!(model)
           t_0 = time()
           for i=1:3
               t = savetime!(model)      # first function called
               println(round(t - t_0, digits=3))
               updatestate!(model, [1])
               periodsleep(model, true)  # last function called
           end
       end;

julia> sim_realtime!(model)
0.0
0.25
0.5
```
