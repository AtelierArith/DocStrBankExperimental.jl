```
inverse(f)
```

Return the inverse of function `f`.

`inverse` supports mapped and broadcasted functions (via `Base.Broadcast.BroadcastFunction` or `Base.Fix1`) and function composition (requires Julia >= 1.6).

# Examples

```jldoctest
julia> foo(x) = inv(exp(-x) + 1);

julia> inv_foo(y) = log(y / (1 - y));

julia> InverseFunctions.inverse(::typeof(foo)) = inv_foo;

julia> InverseFunctions.inverse(::typeof(inv_foo)) = foo;

julia> x = 4.2;

julia> inverse(foo)(foo(x)) ≈ x
true

julia> inverse(inverse(foo)) === foo
true

julia> broadcast_foo = VERSION >= v"1.6" ? Base.Broadcast.BroadcastFunction(foo) : Base.Fix1(broadcast, foo);

julia> X = rand(10);

julia> inverse(broadcast_foo)(broadcast_foo(X)) ≈ X
true

julia> bar = log ∘ foo;

julia> VERSION < v"1.6" || inverse(bar)(bar(x)) ≈ x
true
```

# Implementation

Implementations of `inverse(::typeof(f))` have to satisfy

  * `inverse(f)(f(x)) ≈ x` for all `x` in the domain of `f`, and
  * `inverse(inverse(f))` is defined and `inverse(inverse(f))(x) ≈ f(x)` for all `x` in the domain of `f`.

You can check your implementation with [`InverseFunctions.test_inverse`](@ref).
