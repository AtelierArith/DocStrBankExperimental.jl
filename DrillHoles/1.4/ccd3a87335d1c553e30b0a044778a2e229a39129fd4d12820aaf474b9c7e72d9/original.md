```
desurvey(collar, survey, intervals;
         step=:arc, indip=:auto, outdip=:down,
         inunit=u"m", outunit=inunit, len=nothing,
         geom=:point, radius=1.0u"m")
```

Desurvey drill holes based on `collar`, `survey` and `intervals` tables. Optionally, specify a `step` method, an input dip angle convention `indip`, an output dip angle convention `outdip`, an input unit `inunit` and  an output unit in length units.

The option `len` can be used to composite samples to a given length, and the option `geom` can be used to specify the geometry of each sample.

In the case of `:cylinder` geometry, the option `radius` can be used to specify the radius of each cylinder.

## Step methods

  * `:arc` - spherical arc step
  * `:tan` - simple tanget step

See https://help.seequent.com/Geo/2.1/en-GB/Content/drillholes/desurveying.htm

## Dip conventions

### Input dip angle

  * `:auto` - most frequent dip sign points downwards
  * `:down` - positive dip points downwards
  * `:up`   - positive dip points upwards

### Output dip angle

  * `:down` - positive dip points downwards
  * `:up`   - positive dip points upwards

## Output geometries

  * `:cylinder` - geospatial data with cylinders
  * `:point`    - geospatial data with points
  * `:none`     - data frame with usual columns
