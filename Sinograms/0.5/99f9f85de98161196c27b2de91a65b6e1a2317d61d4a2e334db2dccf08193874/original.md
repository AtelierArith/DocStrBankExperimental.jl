```
fbp(sino::AbstractMatrix ; kwargs...)
```

FBP reconstruction from a parallel-beam sinogram of size `[nr × nϕ]`. Returns an image of size `[nx × ny]`.

# Options

  * `nx` : default `nr`
  * `ny` : default `nx`
  * `kwargs` : passed to `fbp!`
