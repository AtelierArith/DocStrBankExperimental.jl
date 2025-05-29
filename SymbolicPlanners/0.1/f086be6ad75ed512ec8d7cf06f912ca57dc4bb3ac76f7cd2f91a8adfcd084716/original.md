```
LMCut()
```

A landmark-based heuristic [1], which builds on top of the relaxed planning graph heuristic [`HMax`](@ref). This heuristic iteratively finds sets of actions through which any relaxed plan must pass (action landmarks), adding the cost of  the least costly landmark to the total heuristic value. This cost is then subtracted from the cost of each landmark, and the process is repeated until the cost of the relaxed plan is driven to zero. The value of the heuristic is thus the sum of the minimum cost actions across all sets of landmarks.

[1] B. Bonet and H. Geffner, "Landmarks, Critical Paths and Abstractions: What's the Difference Anyway?,"  ICAPS (2009), vol. 19 no. 1, pp. 162-169. [https://doi.org/10.1609/icaps.v19i1.13370](https://doi.org/10.1609/icaps.v19i1.13370)
