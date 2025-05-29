```
Unitify()
```

Add units to columns of the table using bracket syntax. A column named `col [unit]` will be renamed to a unitful column `col` with a valid `unit` from Unitful.jl.

In the case that the `unit` is not recognized by Unitful.jl,  no units are added. Empty brackets are also allowed to represent columns without units, e.g. `col []`.
