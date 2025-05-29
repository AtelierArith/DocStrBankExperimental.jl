```
return!(b::Builder, v::Variable)
return!(b::Builder, v::NewVariable)
```

Push a `Core.ReturnNode` to the current end of `b.to::Canvas`. Requires that the user pass in a `v::Variable` or `v::NewVariable` instance – so perform the correct unpack/tupling before creating a `Core.ReturnNode`.
