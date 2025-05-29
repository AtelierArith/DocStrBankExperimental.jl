```
Index(f::Function, filename::AbstractString, keys...)
```

Create an index from a file with the given keys and automatically close the file.

# Example

```Julia
Index(filename, "shortName", "level") do index
    # Do things with index
end
```
