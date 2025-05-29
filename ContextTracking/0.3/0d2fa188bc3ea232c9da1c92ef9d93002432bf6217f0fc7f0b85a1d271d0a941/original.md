```
@ctx <function definition> [label]
```

Define a function that is context-aware i.e. save the current context before executing the function and restore the context right before returning to the caller. So, if the function modifies the context using (see [`@memo`](@ref)), then the change is not visible the caller. ```
