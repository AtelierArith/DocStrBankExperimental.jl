```
with_logabsdet_jacobian(f, x)
```

Computes both the transformed value of `x` under the transformation `f` and the logarithm of the [volume element](https://en.wikipedia.org/wiki/Volume_element).

For `(y, ladj) = with_logabsdet_jacobian(f, x)`, the following must hold true:

  * `y == f(x)`
  * `ladj` is the `log(abs(det(jacobian(f, x))))`

`with_logabsdet_jacobian` comes with support for broadcasted/mapped functions (via `Base.Broadcast.BroadcastFunction` or `Base.Fix1`) and `ComposedFunction`.

If no volume element is defined/applicable, `with_logabsdet_jacobian(f::F, x::T)` returns [`NoLogAbsDetJacobian{F,T}()`](@ref).

# Examples

```jldoctest a
using ChangesOfVariables

foo(x) = inv(exp(-x) + 1)

function ChangesOfVariables.with_logabsdet_jacobian(::typeof(foo), x)
    y = foo(x)
    ladj = -x + 2 * log(y)
    (y, ladj)
end

x = 4.2
y, ladj_y = with_logabsdet_jacobian(foo, x)

using LinearAlgebra, ForwardDiff
y == foo(x) && ladj_y ≈ log(abs(ForwardDiff.derivative(foo, x)))

# output

true
```

```jldoctest a
X = rand(10)
broadcasted_foo = if VERSION >= v"1.6"
    Base.Broadcast.BroadcastFunction(foo)
else
    Base.Fix1(broadcast, foo)
end
Y, ladj_Y = with_logabsdet_jacobian(broadcasted_foo, X)
Y == broadcasted_foo(X) && ladj_Y ≈ logabsdet(ForwardDiff.jacobian(broadcasted_foo, X))[1]

# output

true
```

```jldoctest a
VERSION < v"1.6" || begin # Support for ∘ requires Julia >= v1.6
    z, ladj_z = with_logabsdet_jacobian(log ∘ foo, x)
    z == log(foo(x)) && ladj_z == ladj_y + with_logabsdet_jacobian(log, y)[2]
end

# output

true
```

Implementations of with*logabsdet*jacobian can be tested (as a `Test.@testset`) using [`ChangesOfVariables.test_with_logabsdet_jacobian`](@ref).
