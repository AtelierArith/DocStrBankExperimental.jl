```
gif_ising2d(; s=rand_ising2d(), k=1.0, β=k*β_ising2d, rng=default_rng(),
    algorithm=default_algorithm(), progress=true,
    nwarmups=0, nskips=10, niters=100, 
    gifname="ising2d.gif", fps=10,
    size=(201.5, 217.5), color=:gist_earth, clim=(-2, 1.1), kwargs...
)
```

creates the gif animation of 2D Ising model.

Example: To create a 200x200 GIF animation, run

```julia
gif_ising2d(s=rand_ising2d(200))
```
