```
SequentialInterpolatedResampling{SequentialSamplingConstraint, InterpolationGrid}
```

Indicates that resampling should be done by first resampling sequentially, then  interpolating the sample to an interpolation grid.

## Fields

  * `sequential_constraint::SequentialSamplingConstraint`. The sequential sampling constraint,   for example `StrictlyIncreasing()`.
  * `grid::InterpolationGrid`. The grid onto which the resampled draw (generated according to   the sequential constraint) is interpolated, for example `RegularGrid(0, 100, 2.5)`.

## Examples

For example, `SequentialInterpolatedResampling(StrictlyIncreasing(), RegularGrid(0:2:100))` indicates a sequential draw that is then interpolated to the grid 0:2:100.
