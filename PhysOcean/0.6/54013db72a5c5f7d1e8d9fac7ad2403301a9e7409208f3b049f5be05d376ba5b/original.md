```
ssh=stericheight(rhoi,z,zlevel,dim::Integer=ndims(rhoi))
```

# Input:

  * `rhoi`: integrated density anomalies (from a call to integraterhoprime)
  * `z`: array of vertical positions
  * `zlevel`: integer for the zlevel on which no motion is assumed
  * `dim`: along which dimension depth is found . If not provided last dimension is used

# Output:

  * `ssh`: steric height. space dimensions as for rhoi in which direction dim is taken out

Compute steric height with respect to given depth level presently provided as index , not depth
