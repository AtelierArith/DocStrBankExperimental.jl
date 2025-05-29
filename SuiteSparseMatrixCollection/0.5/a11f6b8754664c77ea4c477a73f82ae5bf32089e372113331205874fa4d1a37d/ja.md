```
ssmc_matrices(ssmc, group, name)
```

文字列 `group` を含むグループと、文字列 `name` を含む名前の行列の `DataFrame` を返します。

```
ssmc_matrices(ssmc, name)
ssmc_matrices(ssmc, "", name)
```

文字列 `name` を含む名前の行列の `DataFrame` を返します。

```
ssmc_matrices(ssmc, group, "")
```

文字列 `group` を含むグループの行列の `DataFrame` を返します。

例: `ssmc_matrices(ssmc, "HB", "bcsstk")`.
