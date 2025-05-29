```
neighbours(geohash, bits_per_char = 2)
```

Compute the geohashes of the cells neighboring the specified geohash cell. Return a dictionary keyed by "north", "north-east", "east", etc. and with values the geohash string of the corresponding adjacent cell at the same precision and bits per character. Note that cells near the poles will have only five neighbors.
