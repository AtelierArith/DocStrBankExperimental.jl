```
temp_prefix(func::Function)
```

Create a temporary prefix, passing the prefix into the user-defined function so that build/packaging operations can occur within the temporary prefix, which is then cleaned up after all operations are finished.  If the path provided exists already, it will be deleted.

Usage example:

```
out_path = abspath("./libfoo")
temp_prefix() do p
    # <insert build steps here>

    # tarball up the built package
    tarball_path, tarball_hash = package(p, out_path)
end
```
