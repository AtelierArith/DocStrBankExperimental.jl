```
configure_optimisers(model, trainer)
```

Return an optimiser's state initialized for the `model`. It can also return a tuple of `(optimiser, scheduler)`, where `scheduler` is any callable object that takes  the current epoch as input and returns a scalar that will be  set as the learning rate for the next epoch.

# Examples

```julia
using Optimisers, ParameterSchedulers

function Tsunami.configure_optimisers(model::Model, trainer)
    return Optimisers.setup(AdamW(1f-3), model)
end

# Now with a scheduler dropping the learning rate by a factor 10 
# at epochs [50, 100, 200] starting from the initial value of 1e-2
function Tsunami.configure_optimisers(model::Model, trainer)

    function lr_scheduler(epoch)
        if epoch <= 50
            return 1e-2
        elseif epoch <= 100
            return 1e-3
        elseif epoch <= 200
            return 1e-4
        else
            return 1e-5
        end
    end
    
    opt_state = Optimisers.setup(AdamW(), model)
    return opt_state, lr_scheduler
end

# Same as above but using the ParameterSchedulers package.
function Tsunami.configure_optimisers(model::Model, trainer)
    lr_scheduler = ParameterSchedulers.Step(1f-2, 0.1f0, [50, 50, 100])
    opt_state = Optimisers.setup(AdamW(), model)
    return opt_state, lr_scheduler
end
```
