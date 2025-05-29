```
Path() -> SystemPath
Path(fp::Tuple) -> SystemPath
Path(fp::AbstractString) -> AbstractPath
Path(fp::P; overrides...) -> P
```

Responsible for creating the appropriate platform specific path (e.g., [PosixPath](@ref) and [WindowsPath`](@ref) for Unix and Windows systems respectively)
