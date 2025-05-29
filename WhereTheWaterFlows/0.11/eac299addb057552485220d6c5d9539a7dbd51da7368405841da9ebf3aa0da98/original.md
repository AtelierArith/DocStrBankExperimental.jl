```
waterflows(dem, cellarea=fill!(similar(dem),1), flowdir_fn=d8dir_feature;
           feedback_fn=nothing, drain_pits=true, bnd_as_sink=false)
```

Does the water flow routing according the D8 algorithm.  Locations of the `dem` with `NaN`-value are ignored.

args:

  * dem – the DEM (or hydro-potential); array
  * cellarea=cellarea=fill!(similar(dem),1) – the source per cell, defaults to 1.

      * if cellarea is negative in places, flux may go to zero but not below.
      * in areas where no routing takes place, typically NaNs in the dem, cellarea is ignored.  This maybe affects mass-conservation.
      * if using physical units then use a volumetric flux per cell, e.g. m3/s.
      * Alternatively, `cellarea` can be a tuple of arrays. Then they are treated/routed separately, for instance `(water, tracer)`.  All quantities need to be extensive (i.e. additive, e.g. use internal energy and not temperature)
  * flowdir*fn=d8dir*feature – the routing function.  Defaults to the built-in `d8dir_feature`                             function but could be customized

kwargs:

  * feedback*fn – function which is applied to area-value(s) at each cell once all water                of the cell has been accumulated but before the water is routed further downstream.                Signature `(uparea, ij, dir) -> new*uparea`--> for example,`(uparea, ij, dir) -> max(uparea, 0)` would ensure that all                 upareas are non-negative.
  * drain_pits – whether to route through pits (true)
  * bnd*as*sink (true) – whether the domain boundary should be sinks, i.e. adjacent cells                can drain into them, or whether to ignore them.
  * nan*as*sink (true) – whether NaN cells in the DEM should make adjacent cells a sink.
  * stacksize (2^13 * 2^10) – size of the call-stack in *flowrouting*catchments!, which is prone to                StackOverflowError.  Note however, that OutOfMemory errors are likely if increased.

Returns

  * area – upslope area (or a tuple of upslope areas if cellarea is a tuple too)
  * stream-length – length of stream to the farthest source (number of cells traversed)
  * dir – flow direction at each location
  * nout – whether the point has outlflow.  I.e. nout[I]==0 –> I is a pit
  * nin – number of inflow cells
  * sinks – location of sinks as Vector{CartesianIndex{2}}
  * pits – location of pits as Vector{CartesianIndex{2}}
  * c – catchment map (color numbers ∈ 1:length(sinks) are for sinks, others for pits)
  * bnds – boundaries between catchments.  The boundary to the exterior/NaNs is not in here.
  * flowdir*extra*output – extra output of the flowdir_fn, which is `nothing` for the default
