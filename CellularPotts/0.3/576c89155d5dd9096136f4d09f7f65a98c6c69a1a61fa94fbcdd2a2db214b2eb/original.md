```
CellPotts(space, initialCellState, penalties)
```

A data container that holds information to run the cellular potts simulation.

Requires three inputs:

  * `space` – a region where cells can exist, generated using `CellSpace()`.
  * `state` – a table where rows are cells and columns are cell properties, generated using `CellState()`.
  * `penalties` – a vector of penalties to append to the model.
