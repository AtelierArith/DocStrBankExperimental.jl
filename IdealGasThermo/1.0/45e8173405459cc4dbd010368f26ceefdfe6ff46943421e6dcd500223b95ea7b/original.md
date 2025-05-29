```
readThermo(filename)
```

Reads a NASA 9 polynomial thermo definintion file which can be obtained from [NASA thermobuild](https://cearun.grc.nasa.gov/ThermoBuild/index_ds.html)  and returns a dictionary of species.

See [here](https://shepherd.caltech.edu/EDL/PublicResources/sdt/formats/nasa.html)  for typical data format

Usage: If a NASA 9 polynomial definition file `thermo.inp` exists then,

`spec = readThermo("thermo.inp")`

will return a dictionary of species.

`readThermo` only considers 2 temperature ranges  (typically 200-1000 K and 1000-6000 K) but more can be added if needed.
