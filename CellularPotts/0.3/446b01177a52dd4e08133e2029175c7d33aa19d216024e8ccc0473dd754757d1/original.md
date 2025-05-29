```
Penalty
```

An abstract type representing a constraint imposed onto the cellular potts model.

To add a new penalty, a new struct subtyping `Penalty` needs to be defined and the `addPenalty!()` function needs to be extended to include the new penalty.

**Note**: variables associated with a new penalty may need to be offset such that index 0 maps to :Medium, index 1 maps to :Cell1, etc.
