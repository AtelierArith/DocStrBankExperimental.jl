```
test_forward(f, Activity, args...; kwargs...)
```

Test `Enzyme.autodiff` of `f` in `Forward`-mode against finite differences.

`f` has all constraints of the same argument passed to `Enzyme.autodiff`, with additional constraints:

  * If it mutates one of its arguments, it *must* return that argument.

# Arguments

  * `Activity`: the activity of the return value of `f`
  * `args`: Each entry is either an argument to `f`, an activity type accepted by `autodiff`,   or a tuple of the form `(arg, Activity)`, where `Activity` is the activity type of   `arg`. If the activity type specified requires a tangent, a random tangent will be   automatically generated.

# Keywords

  * `rng::AbstractRNG`: The random number generator to use for generating random tangents.
  * `fdm=FiniteDifferences.central_fdm(5, 1)`: The finite differences method to use.
  * `fkwargs`: Keyword arguments to pass to `f`.
  * `rtol`: Relative tolerance for `isapprox`.
  * `atol`: Absolute tolerance for `isapprox`.
  * `testset_name`: Name to use for a testset in which all tests are evaluated.

# Examples

Here we test a rule for a function of scalars. Because we don't provide an activity annotation for `y`, it is assumed to be `Const`.

```julia
using Enzyme, EnzymeTestUtils

x, y = randn(2)
for Tret in (Const, Duplicated, DuplicatedNoNeed), Tx in (Const, Duplicated)
    test_forward(*, Tret, (x, Tx), y)
end
```

Here we test a rule for a function of an array in batch forward-mode:

```julia
x = randn(3)
y = randn()
for Tret in (Const, BatchDuplicated, BatchDuplicatedNoNeed),
    Tx in (Const, BatchDuplicated),
    Ty in (Const, BatchDuplicated)

    test_forward(*, Tret, (x, Tx), (y, Ty))
end
```
