Lambda cases.

e.g.

```julia
    xs = [(1, 2), (1, 3), (1, 4)]
    map((@λ (1, x) => x), xs)
    # => [2, 3, 4]

    (2, 3) |> @λ begin
        1 => 2
        2 => 7
        (a, b) => a + b
    end
    # => 5
```
