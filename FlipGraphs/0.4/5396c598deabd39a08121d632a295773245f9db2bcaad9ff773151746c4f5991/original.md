```
struct FGVertex
```

A *vertex* in a `FlipGraph`. 

A `FGVertex` is composed of a representant (`DeltaComplex`) of the isotopy class of that vertex.  The representant has been relabeled with one of the canonical labeling obtained by an adaptation of *McKay's Algorithm*. Additionally, the `FGVertex` contains the number of labeling that are output by the respective *McKay's Algorithms*.
