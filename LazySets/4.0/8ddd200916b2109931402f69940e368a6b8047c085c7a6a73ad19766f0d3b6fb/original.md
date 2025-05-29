```
ispolyhedral(B::Bloating)
```

Check whether a bloated set is polyhedral.

### Input

  * `B` – bloated set

### Output

`true` if the set is polyhedral.

### Algorithm

We check the sufficient condition that the base set is polyhedral and that the norm for bloating is either 1-norm or the infinity norm.
