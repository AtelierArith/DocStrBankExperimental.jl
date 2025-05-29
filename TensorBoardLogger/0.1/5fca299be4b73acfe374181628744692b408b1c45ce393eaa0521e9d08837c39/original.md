`with_TBLogger_hold_step(f, [step]; step_at_end::Bool=true)` Context function to ease control of logging steps and synchronization. Amount of step increment can be controlled via `set_step_increment!``.

Example:

```julia
with_logger(lg) do
    for epoch in 1:10
        for i=1:100
            # increments global_step by default
            with_TBLogger_hold_step() do
                # all of these are logged at the same global_step
                # and the logger global_step is only then increased
                @info "train1/scalar" i=i
                @info "train2/scalar" i2=i^2
                @info "train3/scalar" i3=i^3
            end
        end
        # step increment at end can be disabled for easy train/test sync
        with_TBLogger_hold_step(;step_at_end=false) do
            # all of these are logged at the same global_step
            # and the logger global_step is only then increased
            @info "test1/scalar" i=i
            @info "test2/scalar" i2=i^2
            @info "test3/scalar" i3=i^3
        end
    end
end
```
