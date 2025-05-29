```
register!([:datatype|:predicate|:function|:modifier|:converter], name, x)
```

Register `x` as a global datatype, predicate, function or modifier, or term converter under the specified `name`.

!!! warning "Top-Level Only"
    Because `register!` defines new methods, it should only be called at the top-level in order to avoid world-age errors.


!!! warning "Precompilation Not Supported"
    Because `register!` evaluates code in the `PDDL` module, it will lead to precompilation errors when used in another module. For this reason, the `@register` macro is preferred, and this function should only be used in scripting contexts.

