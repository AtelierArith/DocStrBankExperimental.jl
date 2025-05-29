```
filaments3D!(obj; radius = 0.8, rand_offset=0.05, rel_theta=1.0, num_filaments=50, apply_seed=true, thickness=0.8)
```

Create a 3D representation of filaments.

# Arguments

  * `obj`: A 3D array representing the volume into which the filaments will be added.
  * `radius`: A tuple of real numbers (or a single real number) representing the relative radius of the volume in which the filaments will be created.    Default is 0.8. If a tuple is used, the filamets will be created in a corresponding elliptical volume.   Note that the radius is only enforced in the version `filaments3D` which creates the array rather than adding.
  * `rand_offset`: A tuple of real numbers representing the random offsets of the filaments in relation to the size. Default is 0.05.
  * `rel_theta`: A real number representing the relative theta range of the filaments. Default is 1.0.
  * `num_filaments`: An integer representing the number of filaments to be created. Default is 50.
  * `apply_seed`: A boolean representing whether to apply a seed to the random number generator. Default is true.
  * `thickness`: A real number representing the thickness of the filaments in pixels. Default is 0.8.

The result is added to the obj input array

# Example

```julia

# create a 100x100x100 volume with 10 filaments where only the central slice has a random arrangement of filaments
julia> obj = rand(100,100,100); # create an array of random numbers
julia> filaments3D!(obj; num_filaments=10, rel_theta=0, rand_offset=(0.1,0.1,0), intensity=2.0);

```
