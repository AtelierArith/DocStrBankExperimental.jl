```
rij_per_unit(i::AbstractString, j::AbstractString, net::Network)

resistance(net[(i,j)]) / net.Zbase
```

Resistance of edge i-j normalized by `net.Zbase`
