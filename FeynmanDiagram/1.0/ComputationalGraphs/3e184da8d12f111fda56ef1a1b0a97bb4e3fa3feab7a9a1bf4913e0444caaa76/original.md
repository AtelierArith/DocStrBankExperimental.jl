```
function external_vertex(ops::OperatorProduct;
    name="", factor=one(_dtype.factor), weight=zero(_dtype.weight), operator=Sum())
```

Create a ExternalVertex-type FeynmanGraph from given OperatorProduct `ops`, including several quantum operators for an purely external vertex.
