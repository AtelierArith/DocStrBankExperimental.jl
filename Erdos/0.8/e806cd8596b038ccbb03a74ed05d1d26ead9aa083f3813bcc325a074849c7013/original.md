```
community_detection_nback(g, k)
```

Community detection using the spectral properties of the non-backtracking matrix of graph `g` (see [Krzakala et al.](http://www.pnas.org/content/110/52/20935.short)). `k` is the number of communities to detect.

See also [`community_detection_bethe`](@ref) for a related community ddetection algorithm.

Returns a vector with the vertex assignments in the communities.
