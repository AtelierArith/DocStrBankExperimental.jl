```
Topology
```

Type of basis shape to create non-tensor H1 element basis. One of `LINE`, `TRIANGLE`, `QUAD`, `TET`, `PYRAMID`, `PRISM`, or `HEX`.

The dimension can be extracted with bitshift:

```
dim = Int(topology) >> 16
```
