```
req = @request expr
```

Create a request of internal results wanted from a function. Considering the function presented as example for [`@espy`](@ref), examples of possible syntax include

```
req       = @request gp(s,z,material(a,b))
req       = @request gp(s)
req       = @request gp(material(a))
```

The first expression can be read as follows: "In the function, there is a `do` loop over variable `igp`, and within this loop a call to a function `material`.  Results `s` and `z` are wanted from within the loop, and results `a` and `b` from within `material`.

The corresponding datastructure containing the results for each element is a nesting of `NTuples` and `NamedTuples`,  and can be accessed as `out.gp[igp].material.a` and so forth.        

See also: [`@espy`](@ref), [`@espydbg`](@ref)
