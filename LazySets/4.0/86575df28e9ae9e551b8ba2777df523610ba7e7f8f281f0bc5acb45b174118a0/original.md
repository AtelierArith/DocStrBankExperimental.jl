```
constraints_list(C::Complement)
```

Return the list of constraints of the complement of a set.

### Input

  * `C` – complement of a set

### Output

A vector of linear constraints.

### Notes

The method requires that the list of constraints of the complemented set can be obtained. Then, each constraint is complemented and returned in the output vector. The set union of this array corresponds to the concrete set complement.
