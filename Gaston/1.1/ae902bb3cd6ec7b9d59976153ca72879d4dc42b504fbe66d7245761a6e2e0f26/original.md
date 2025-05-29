```
plot([x,] y, [z,] [axes,] [supp,] [dims,] [h,] [curve]) -> Gaston.Figure
```

Plots data `x`, `y`, and optionally `z` and `supp`, in two or three dimensions as specified by `dims`, with axes configuration `axes`, and curve configuration `curve`, on the figure with handle `h`.

If `x` is omitted, then `x=1:length(t)` is assumed.

```
plot(x, f::Function, args...) -> Gaston.Figure
```

Assume `y = f.(x)`.

```
plot(c, args...) -> Gaston.Figure
```

If `c` is a complex vector, plot its real part vs its imaginary part.

```
plot(P::Matrix{Union{Gaston.Figure}, Nothing}) -> Gaston.Figure
```

Create a 'muliplot' with the layout in `P`. Returns a new figure.
