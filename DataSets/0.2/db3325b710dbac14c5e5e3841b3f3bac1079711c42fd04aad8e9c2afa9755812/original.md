```
newfile(func)
newfile(func, ctx)
```

Create a new temporary `Blob` object which may be later assigned to a permanent location in a `BlobTree`. If not assigned to a permanent location, the temporary file is cleaned up during garbage collection.

# Example

```
tree[path"some/demo/path.txt"] = newfile() do io
    println(io, "Hi there!")
end
```
