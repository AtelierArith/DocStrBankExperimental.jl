```
inrelativeinterior(p::VRepElement, h::HRepElement; tol)
```

Returns whether `p` is in the relative interior of `h`. If `h` is an hyperplane, it is equivalent to `p in h` since the relative interior of an hyperplane is itself. If `h` is an halfspace, it is equivalent to `ininterior(p, h)`.

```
inrelativeinterior(p::VRepElement, h::HRep; tol)
```

Returns whether `p` is in the relative interior of `h`, e.g. in the relative interior of all the hyperplanes and halfspaces supporting `h`.
