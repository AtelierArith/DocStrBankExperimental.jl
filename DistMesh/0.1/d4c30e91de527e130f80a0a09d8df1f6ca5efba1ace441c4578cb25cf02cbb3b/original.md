```
DistMeshSetup
```

Takes Keyword arguments as follows:

```
iso (default: 0): Value of which to extract the isosurface, inside surface is negative
deltat (default: 0.1): the fraction of edge displacement to apply each iteration
sort (default:false): If true and no fixed points, sort points using a hilbert sort.
sort_interval (default:20) Use hilbert sort after the specified retriangulations
distribution (default: :regular) Initial point distribution, either :regular or :packed.
```
