```
get_linear_segment_color(dict, n)
```

Get the RGB color for value `n` from a dictionary of linear color segments.

This following is a dictionary where red increases from 0 to 1 over the bottom half, green does the same over the middle half, and blue over the top half:

```
cdict = Dict(:red  => ((0.0,  0.0,  0.0),
                       (0.5,  1.0,  1.0),
                       (1.0,  1.0,  1.0)),
            :green => ((0.0,  0.0,  0.0),
                       (0.25, 0.0,  0.0),
                       (0.75, 1.0,  1.0),
                       (1.0,  1.0,  1.0)),
            :blue =>  ((0.0,  0.0,  0.0),
                       (0.5,  0.0,  0.0),
                       (1.0,  1.0,  1.0)))
```

The value of RGB component at every value of `n` is defined by a set of tuples. In each tuple, the first number is `x`. Colors are linearly interpolated in bands between consecutive values of `x`; if the first tuple is given by `(Z, A, B)` and the second tuple by `(X, C, D)`, the color of a point `n` between Z and X will be given by `(n - Z) / (X - Z) * (C - B) + B`.

For example, given an entry like this:

```
:red  => ((0.0, 0.0, 0.0),
          (0.5, 1.0, 1.0),
          (1.0, 1.0, 1.0))
```

and if `n` = 0.75, we return 1.0; 0.75 is between the second and third segments, but we'd already reached 1.0 (segment 2) when `n` was 0.5.
