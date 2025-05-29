```
compare_fields(s1, s2; silent::Bool = false)
```

Compare data for each data field in 2 structs of the same type.

**Arguments:**

  * `s1`:     struct 1
  * `s2`:     struct 2
  * `silent`: (optional) if true, no summary print out

**Returns:**

  * `N_dif`: if `silent = false`, number of different fields
