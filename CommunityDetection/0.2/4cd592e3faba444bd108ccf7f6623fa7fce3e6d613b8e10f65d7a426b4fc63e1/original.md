```
community_detection_nback(g::AbstractGraph, k::Int)
```

Return an array, indexed by vertex, containing commmunity assignments for graph `g` detecting `k` communities. Community detection is performed using the spectral properties of the  non-backtracking matrix of `g`.

### References

  * [Krzakala et al.](http://www.pnas.org/content/110/52/20935.short)
