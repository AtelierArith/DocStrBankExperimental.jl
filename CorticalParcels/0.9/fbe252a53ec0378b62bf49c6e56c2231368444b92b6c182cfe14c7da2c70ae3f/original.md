```
 resize!(p, desired_size, A, neighbors)
```

Resize a `Parcel` `p`, guided by an adjacency matrix and an adjacency list,  by repeated dilation or erosion until `p` reaches `desired_size`.
