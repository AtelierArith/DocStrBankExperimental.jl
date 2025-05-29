```
vispts(coord, colormap::Symbol=:viridis, colorby::String="-1", attr::Vector=[-1], 
    psize::Float32=1f-2, sample_n::Int=1000000)
```

## Description:

Visualize the particles in a browser/VSCode using WGLMakie.

  * coord: The coordinates of the particles. It should be a 2D or 3D array of shape (n, m),

where n is the number of particles and m is the dimension (2 or 3).

  * colormap [option]: The colormap to use for the visualization. Default is :viridis.
  * colorby [option]: The attribute to color the particles by. Default is "-1", which means   the z-coordinate. If attr is provided, it will be used instead.
  * attr [option]: The attributes of the particles. It should be a vector of length n.
  * psize [option]: The size of the particles in the visualization. Default is 1e-2.
  * sample_n [option]: The number of particles to sample for visualization. Default is 1,000,000.   If the number of particles exceeds this value, a random sample will be taken.

## Examples:

```julia
vispts(rand(10, 3))
vispts(rand(10, 3), colorby="random vals", attr=rand(10), psize=1f0, sample_n=5, colormap=:jet)
```
