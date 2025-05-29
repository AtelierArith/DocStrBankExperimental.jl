```
cost,i1,i2 = fastdtw(seq1,seq2,dist,radius)
```

Perform dynamic-time warping using the FastDTW algorithm to measure the distance between two sequences. Note that regular DTW often performs better than FastDTW https://arxiv.org/abs/2003.11246

Computes FastDTW approximation to the DTW, described in Salvador & Chan, Intelligent Data Analysis (2007).

See also [`dtw`](@ref), [`dtw_cost`](@ref), [`dtwnn`](@ref).
