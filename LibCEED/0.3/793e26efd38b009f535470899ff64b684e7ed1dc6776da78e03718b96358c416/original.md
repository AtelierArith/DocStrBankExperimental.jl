```
@witharray(v_arr=v, [size=(dims...)], [mtype=MEM_HOST], body)
```

Executes `body`, having extracted the contents of the [`CeedVector`](@ref) `v` as an array with name `v_arr`. If the [`memory type`](@ref MemType) `mtype` is not provided, `MEM_HOST` will be used. If the size is not specified, a flat vector will be assumed.

# Examples

Negate the contents of `CeedVector` `v`:

```
@witharray v_arr=v v_arr .*= -1.0
```
