```
avgseq(S; [method=:dtw, dist=SqEuclidean(), radius=10, center=:medoid, dtwradius=nothing, progress=false])
```

Return a sequence representing the average of the sequences in `S` using the dba method for sequence averaging. Supports `method=:dtw` for vanilla dtw and `method=:fastdtw` for fast dtw approximation when performing the sequence comparisons. With `center=:medoid`, finds the medoid as the sequence to use as the initial center, and with `center=:rand` selects a random element in `S` as the initial center.

# Args

  * `S` An array of sequences to average
  * `method` (keyword) The method of dynamic time warping to use
  * `dist` (keyword) Any distance function implementing the `SemiMetric` interface from the `Distances` package
  * `radius` (keyword) The radius to use for the fast dtw method; argument unused when method=:dtw
  * `center` (keyword) The method used to select the initial center of the sequences in `S`
  * `dtwradius` (keyword) How far a time step can be mapped when comparing sequences; passed directly to `DTW` function from `DynamicAxisWarping`; if set to `nothing`, the length of the longest sequence will be used, effectively removing the radius restriction
  * `progress` Whether to show the progress coming from `dba`
