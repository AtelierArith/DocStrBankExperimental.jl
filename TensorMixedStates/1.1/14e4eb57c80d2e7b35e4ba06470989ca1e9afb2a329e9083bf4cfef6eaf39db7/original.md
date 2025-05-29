```
expect(::State, obs)
```

Compute expectation values of `obs` on the given state.

# Examples

```
expect(state, X(1)*Y(2) + Y(1)*Z(3))
expect(state, [X(1)*Y(2), X(3), Z(1)*X(2)])
```
