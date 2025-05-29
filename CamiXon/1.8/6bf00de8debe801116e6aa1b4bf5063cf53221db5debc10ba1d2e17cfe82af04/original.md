```
lc_primitivetype(o::Any)
```

Lowest comon primitive type of Any Type

#### Examples:

```
julia> o = ([1//2, 1//3]; (1//4, 1//1, 1//6));
julia> lc_primitivetype(o)
Int64
```
