```
datum_shift_ECEF(dest_datum, source_datum)
```

Return a transformation object which transforms ECEF points from `source_datum` to `dest_datum`.  The function should attempt to supply the current publicly accepted best estimate.

Note that the best known version of a datum transformation will inherently improve with time (see below), so we *cannot simultaneously* guarantee that:

1. We return the best publicly accepted version of a datum shift.
2. We return the same thing in future versions of Geodesy.jl.

This function will attempt to satisfy condition 1. rather than 2.; if you want a stable version of a transformation you should use one of the lower level functions, for example, `GDA94_from_ITRF_Dawson2010()`.

### Important note about accuracy

If you care about accuracy, you should *always* store long term archival data in the source datum where possible, along with metadata defining the full datum and coordinate system in use.  The time to do a datum shift is when you want to compare information from two different datums.

Why all this bother about inaccuracy? The errors are twofold: First, the parameters of a datum shift come from a physical measurement process. Typically this involves measuring the coordinates of some physical locations in *both* datums, and a physical measurement procedure is always subject to some inaccuracy. Second, these **tie points** are used to infer a compact representation of the datum shift, with as few numerical parameters as possible. A small number of parameters will result in an overly smooth representation; this modelling error is a second source of inaccuracy.  Both these errors can be reduced if you choose to measure more tie points or improve the complexity of the numerical model at a future date.
