`gappy_intervals(pts::Vector{Float64}; gaptol=8, minlen=128, coalesce_tol=0.005) -> Vector{NTuple{2,Float64}}`

Given a collection of (sorted!) 1D measurement locations `pts`, returns an attempt at automatically partitioning those points into sub-segments without large measurement gaps. 

Keyword arguments:

  * `gaptol`: If the largest gap between adjacent points is bigger than `gaptol*median(abs, diff(pts))`, then split that domain to two intervals.
  * `minlen`: If the resulting number of points in an interval after splitting is less than `minlen`, completely discard that interval.
  * `coalesce_tol`: If, after partitioning, two intervals (a1, b1) and (a2, b2) are sufficiently close that (a2 - b1) < coalesce_tol*max(b1-a1, b2-a2)`, re-combine those intervals.

This is a **very heuristic** function, that is really offered just as a convenience for exploratory analysis. Please do not automatically use this on something important without inspecting the result.
