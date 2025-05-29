```
@global_fixture [option=val ...] <name> begin ... end
@global_fixture [option=val ...] <name> for x in fx1, (y, z) in fx2 ... end
```

Create a global fixture (a fixture set up once before all the testcases that use it and torn down after they finish).

The body must contain a single call to [`@produce`](@ref), producing a single value.

The iterables in the `for` loop are either fixtures (constant of global only), iterable objects or pairs of two iterables used to parametrize the fixture.

Available options:

`instant_teardown :: Bool`: if `true`, the part of the fixture body after the [`@produce`](@ref) will be executed immediately.

Returns a [`GlobalFixture`](@ref) object.
