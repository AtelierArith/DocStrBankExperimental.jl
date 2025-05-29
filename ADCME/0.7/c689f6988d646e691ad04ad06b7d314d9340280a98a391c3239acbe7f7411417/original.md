```
get_library_name(filename::AbstractString)
```

Returns the OS-dependent library name 

# Example

```
get_library_name("mylibrary")
```

  * Windows: `mylibrary.dll`
  * MacOS: `libmylibrary.dylib`
  * Linux: `libmylibrary.so`
