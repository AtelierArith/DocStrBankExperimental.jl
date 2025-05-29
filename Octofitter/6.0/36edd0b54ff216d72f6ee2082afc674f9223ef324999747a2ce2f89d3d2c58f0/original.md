```
plotchains(
    chain, planet_key;
    N=1500,
    ii = rand(1:size(chain,1)*size(chain,3), N),
    color=length(model.system.planets) == 0 || !haskey(chain, string(planet_key)*"_a") ? nothing : string(planet_key)*"_a",
    colorbartitle=color,
    clims=nothing,
    cmap=:plasma,
    alpha=30/length(ii),
    attime=nothing,
    kwargs...,
)
```

Draw samples from a posterior chain for a given planet given by name `planet_key` and visualize them in some way. Use `kind` to control what plot is made. A few options: :astrometry, :radvel, :trueanom, :meananom, :eccanom, :x, :y, :z, (:x, :y), :raoff, :decoff, :pmra, :pmdec, :accra, :accdec, :radvel, :posangle, :projectedseparation. See PlanetOrbits documentation for more details.

Inputs:

  * chain                   The chain to draw from
  * planet_key              Planet name in the model (symbol)
  * N=1500                  Number of samples to draw for the plot
  * kind=nothing            Specify what kind of plot to make.
  * ii=...                  Specific row numbers to use, if you want to e.g. plot the same 100 samples in a few different plots
  * color="planet*key*a"   Column name to to map colors to. Semi-major axis by default but can be any column or an arbitrary array.
  * colorbartitle=color     Name for colourbar
  * clims=nothing           Tuple of colour limits (min and max)
  * cmap=:plasma            Colormap
  * alpha=...               Transparency of the lines
