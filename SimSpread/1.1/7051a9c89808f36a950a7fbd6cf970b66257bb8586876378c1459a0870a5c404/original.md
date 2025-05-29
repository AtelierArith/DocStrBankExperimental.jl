```
save(filepath::String, fidx::Int64, yhat::NamedMatrix, y::NamedMatrix; delimiter::Char='	')
```

Store cross-valudation predictions as a table in the given file path.

# Arguments

  * `filepath::String`: Output file path
  * `fidx::Int64`: Numeric fold ID
  * `yhat::NamedArray`: Predicted source-target bipartite adjacency matrix
  * `y::NamedArray`: Ground-truth source-target bipartite adjacency matrix
  * `delimiter::Char`: Delimiter used to write table (default = '\t')

# Extended help

Table format is:

```
fold, source, target, score, label
```
