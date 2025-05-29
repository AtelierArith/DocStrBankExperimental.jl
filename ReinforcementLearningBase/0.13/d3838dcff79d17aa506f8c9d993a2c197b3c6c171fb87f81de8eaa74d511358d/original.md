```
state(env, style=[DefaultStateStyle(env)], player=[current_player(env)])
```

The state can be of any type. However, most neural network based algorithms assume an `AbstractArray` is returned. For environments with many different states provided (inner state, information state, etc), users need to provide `style` to declare which kind of state they want.

!!! warning
    The state **may** be reused and be mutated at each step. Always remember to make a copy if this is not what you expect.

