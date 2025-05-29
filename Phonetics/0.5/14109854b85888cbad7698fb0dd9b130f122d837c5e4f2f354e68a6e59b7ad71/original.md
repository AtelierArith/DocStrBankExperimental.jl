```
acdist(s1, s2; [method=:dtw, dist=SqEuclidean(), radius=10])
```

Calculate the acoustic distance between `s1` and `s2` with `method` version of dynamic time warping and `dist` as the interior distance function. Using `method=:dtw` uses vanilla dynamic time warping, while `method=:fastdtw` uses the fast dtw approximation. Note that this is not a true mathematical distance metric because dynamic time warping does not necessarily satisfy the triangle inequality, nor does it guarantee the identity of indiscernibles.

# Args

  * `s1` Features-by-time array of first sound to compare
  * `s2` Features-by-time array of second sound to compare
  * `method` (keyword) Which method of dynamic time warping to use
  * `dist` (keyword) Any distance function implementing the `SemiMetric` interface from the `Distances` package
  * `dtwradius` (keyword) maximum warping radius for vanilla dynamic timew warping; if no value passed, no warping constraint is used argument unused when method=:fastdtw
  * `fastradius` (keyword) The radius to use for the fast dtw method; argument unused when method=:dtw
