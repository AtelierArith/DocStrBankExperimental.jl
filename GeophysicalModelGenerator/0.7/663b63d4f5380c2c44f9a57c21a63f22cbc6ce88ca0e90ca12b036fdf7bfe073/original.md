```
pvd = movie_paraview(; name="Movie", pvd=pvd, Finalize::Bool=false, Initialize::Bool=true)
```

If you want to make a movie of your data set, you can use this routine to initialize and to finalize the movie-file. It will create a `*.pvd` file, which you can open in Paraview 

Individual timesteps are added to the movie by passing `pvd` and the time of the timestep to the `write_paraview` routine.

# Example

Usually this is used inside a `*.jl` script, as in this pseudo-example:

```julia
movie = movie_paraview(name="Movie", Initialize=true)
for itime=1:10
    name = "test"*string(itime)
    movie = write_paraview(Data, name, pvd=movie, time=itime)
end
movie_paraview(pvd=movie, Finalize=true)
```
