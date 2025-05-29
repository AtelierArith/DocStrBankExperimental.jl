```
ssmc_matrices(ssmc, group, name)
```

Return a `DataFrame` of matrices whose group contains the string `group` and whose name contains the string `name`.

```
ssmc_matrices(ssmc, name)
ssmc_matrices(ssmc, "", name)
```

Return a `DataFrame` of matrices whose name contains the string `name`.

```
ssmc_matrices(ssmc, group, "")
```

Return a `DataFrame` of matrices whose group contains the string `group`.

Example: `ssmc_matrices(ssmc, "HB", "bcsstk")`.
