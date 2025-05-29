```
animate(filename::AbstractString,
        plots::Vector{Plot2D};
        rate=10)

animate(plots::Vector{Plot2D};rate=10)
```

Make an `.mp4` video from `plots`, with frame rate `rate`

If "filename" is given, the movie file will be stored there. Otherwise, the movie will be opened.

# Example

```julia
X = cumsum(randn(100000))
Y = cumsum(randn(100000))
plots = [Plot(Path(X[1:t],Y[1:t])) for t=10:10:10000]
animate(plots)
```
