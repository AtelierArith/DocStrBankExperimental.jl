```
blockerr(lengt, nsegmentts; <keyword arguments>)
```

Blocker code to divide the data into segments 

...

# Arguments

  * `lengt::Int64`: input length of a time series
  * `nsegments::Int64`: number of segments
  * `overlap::Float64 = 0.0`: fraction of overlap between segments, between 0.0 and 1.0

...

...

# Outputs

  * `seq::Vector{Int64}`: Beginning index for each segment
  * `seg_len::Int64`: length of the segments
  * `ov::Float64`: overlap that actually resulted (≈`overlap`, above)

...
