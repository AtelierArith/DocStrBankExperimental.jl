```
TRI(dem::Matrix{<:Real})
```

TRI stands for Terrain Ruggedness Index, which measures the difference between a central pixel and its surrounding cells. This algorithm uses the square root of the sum of the square of the difference between a central pixel and its surrounding cells. This is recommended for terrestrial use cases.
