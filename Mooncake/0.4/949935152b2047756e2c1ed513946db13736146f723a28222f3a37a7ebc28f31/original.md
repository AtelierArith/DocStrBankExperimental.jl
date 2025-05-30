```
value_and_pullback!!(cache::Cache, ȳ, f, x...)
```

!!! info
    If `f(x...)` returns a scalar, you should use [`value_and_gradient!!`](@ref), not this function.


Computes a 2-tuple. The first element is `f(x...)`, and the second is a tuple containing the pullback of `f` applied to `ȳ`. The first element is the component of the pullback associated to any fields of `f`, the second w.r.t the first element of `x`, etc.

There are no restrictions on what `y = f(x...)` is permitted to return. However, `ȳ` must be an acceptable tangent for `y`. This means that, for example, it must be true that `tangent_type(typeof(y)) == typeof(ȳ)`.

As with all functionality in Mooncake, if `f` modifes itself or `x`, `value_and_gradient!!` will return both to their original state as part of the process of computing the gradient.

!!! info
    `cache` must be the output of [`prepare_pullback_cache`](@ref), and (fields of) `f` and `x` must be of the same size and shape as those used to construct the `cache`. This is to ensure that the gradient can be written to the memory allocated when the `cache` was built.


!!! warning
    `cache` owns any mutable state returned by this function, meaning that mutable components of values returned by it will be mutated if you run this function again with different arguments. Therefore, if you need to keep the values returned by this function around over multiple calls to this function with the same `cache`, you should take a copy (using `copy` or `deepcopy`) of them before calling again.


# Example Usage

```jldoctest
f(x, y) = sum(x .* y)
x = [2.0, 2.0]
y = [1.0, 1.0]
cache = Mooncake.prepare_pullback_cache(f, x, y)
Mooncake.value_and_pullback!!(cache, 1.0, f, x, y)

# output

(4.0, (NoTangent(), [1.0, 1.0], [2.0, 2.0]))
```
