```
Centered()
```

Pass centered as a dimesion range to automatically center a dimension along that axis.

Example:

```julia
cube = load("abc.fits", (X=Centered(), Y=Centered(), Pol=[:I, :Q, :U]))
```

In that case, cube will have dimsions with the centre of the image at 0 in both the X and Y axes.
