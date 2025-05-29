```
compiled(domain, state)
compiled(domain, problem)
```

Compile a `domain` and `state` and return the resulting compiled domain and compiled state. A `problem` maybe provided instead of a state.

!!! warning "Top-Level Only"
    Because `compiled` defines new types and methods, it should only be called at the top-level in order to avoid world-age errors.


!!! warning "Precompilation Not Supported"
    Because `compiled` evaluates code in the `PDDL` module, it will lead to precompilation errors when used in another module or package. Modules which call `compiled` should hence disable precompilation.

