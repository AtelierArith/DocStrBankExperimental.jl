```
field_amplitude(f, a, b)
```

Compute the time integral of the field amplitude according to

$$
\int_a^b\diff{t}F(t) = -[A(b) - A(a)],
$$

where $A(t)$ is the [`vector_potential`](@ref).
