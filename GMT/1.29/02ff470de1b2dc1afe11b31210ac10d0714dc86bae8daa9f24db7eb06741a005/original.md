```
gravfft(cmd0::String="", arg1=nothing, arg2=nothing; kwargs...)
```

Spectral calculations of gravity, isostasy, admittance, and coherence for grids.

## Parameters

  * **D** | **density** :: [Type => Str | GMTgrid]

    Sets body density in SI. Provide either a constant density or a grid with a variable one.
  * **E** | **n_terms** :: [Type => Number]

    Number of terms used in Parker expansion [Default = 3].
  * **F** | **field** :: [Type => Str | Tuple]

    Specify desired geopotential field: compute geoid rather than gravity
  * **I** | **admittance** :: [Type => Number]

    Use ingrid2 and ingrid1 (a grid with topography/bathymetry) to estimate admittance|coherence and return a GMTdataset.
  * **N** | **dimensions** | **inquire** :: [Type => Str]         $Arg = [a|f|m|r|s|nx/ny][+a|[+d|h|l][+e|n|m][+twidth][+v][+w[suffix]][+z[p]]$

    Choose or inquire about suitable grid dimensions for FFT and set optional parameters. Control the FFT dimension:
  * **Q** | **flex_topo** | **flexural_topography** :: [Type => Bool]

    Computes grid with the flexural topography.
  * **S** | **subplate** | **subplate_load** :: [Type => Bool]

    Computes predicted gravity or geoid grid due to a subplate load produced by the current bathymetry and the theoretical model.
  * **T** | **topo_load** :: [Type => Str]

    Compute the isostatic compensation from the topography load (input grid file) on an elastic plate of thickness `te`.
  * **W** | **level** :: [Type => Number]

    Set water depth (or observation height) relative to topography in meters [0]. Append k to indicate km.
  * **Z** | **moho_depth** :: [Type => Number]

    Moho [and swell] average compensation depths (in meters positive down).
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).

To see the full documentation type: $@? gravfft$

### Example. Compute the gravity effect of the Gorringe bank.

```julia
    G = grdcut("@earth_relief_10m", region=(-12.5,-10,35.5,37.5));
	G2 = gravfft(G, density=1700, F=(faa=6,slab=4), f=:g);
	imshow(G2)
```
