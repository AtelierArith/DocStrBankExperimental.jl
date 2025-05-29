```
@local_fixture <name> begin ... end
@local_fixture <name> for x in fx1, (y, z) in fx2 ... end
```

Create a local fixture (a fixture set up before each testcase that uses it and torn down afterwards).

The body must contain a single call to [`@produce`](@ref), producing a single value.

The iterables in the `for` loop are either fixtures (constant of global only), iterable objects or pairs of two iterables used to parametrize the fixture.

Returns a [`LocalFixture`](@ref) object.
