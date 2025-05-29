```
Path() -> SystemPath
Path(fp::Tuple) -> SystemPath
Path(fp::AbstractString) -> AbstractPath
Path(fp::P; overrides...) -> P
```

プラットフォーム固有の適切なパスを作成する責任があります（例：[PosixPath](@ref) と [WindowsPath](@ref) はそれぞれUnixおよびWindowsシステム用）
