```
constraints_list(ilm::InverseLinearMap)
```

Return a list of constraints of a (polyhedral) inverse linear map.

### Input

  * `ilm` – inverse linear map

### Output

A list of constraints of the inverse linear map.

### Algorithm

We fall back to a concrete set representation and apply `linear_map_inverse`.
