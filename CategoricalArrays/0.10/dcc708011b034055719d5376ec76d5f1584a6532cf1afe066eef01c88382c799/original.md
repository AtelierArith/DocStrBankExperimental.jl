```
recode!(dest::AbstractArray, src::AbstractArray[, default::Any], pairs::Pair...)
```

Fill `dest` with elements from `src`, replacing those matching a key of `pairs` with the corresponding value.

For each `Pair` in `pairs`, if the element is equal to (according to `isequal`)) the key (first item of the pair) or to one of its entries if it is a collection, then the corresponding value (second item) is copied to `dest`. If the element matches no key and `default` is not provided or `nothing`, it is copied as-is; if `default` is specified, it is used in place of the original element. `dest` and `src` must be of the same length, but not necessarily of the same type. Elements of `src` as well as values from `pairs` will be `convert`ed when possible on assignment. If an element matches more than one key, the first match is used.

```
recode!(dest::CategoricalArray, src::AbstractArray[, default::Any], pairs::Pair...)
```

If `dest` is a `CategoricalArray` then the ordering of resulting levels is determined by the order of passed `pairs` and `default` will be the last level if provided.

```
recode!(dest::AbstractArray, src::AbstractArray{>:Missing}[, default::Any], pairs::Pair...)
```

If `src` contains missing values, they are never replaced with `default`: use `missing` in a pair to recode them.
