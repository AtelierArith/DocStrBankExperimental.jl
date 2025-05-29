```
@flow path="path/to/file" expr
```

A macro that checks if the file in the `path` exists and if it didn't change and only runs the `expr` if needed. After the first run, create a file with the same name as `path` with the .hash suffix, and writes the sha256 sum hash.

# Example

```jldoctest
julia> filePath, _ = mktemp();

julia> @flow path=filePath begin
           println("This should only show once")
           write(filePath, "some random text")
       end
This should only show once
64

julia> @flow path=filePath begin
           println("This should only show once")
           write(filePath, "some random text")
       end
```
