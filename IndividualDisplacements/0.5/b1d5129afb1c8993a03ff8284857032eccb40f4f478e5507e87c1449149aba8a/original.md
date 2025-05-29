```
postprocess_xy(sol,P::FlowFields,D::NamedTuple; id=missing, T=missing)
```

Copy `sol` to a `DataFrame` & map position to x,y coordinates, and define time axis for a simple doubly periodic domain
