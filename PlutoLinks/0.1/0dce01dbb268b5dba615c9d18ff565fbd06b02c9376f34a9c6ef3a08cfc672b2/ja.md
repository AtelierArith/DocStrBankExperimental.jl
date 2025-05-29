Juliaソースファイルを監視し、その内容をモジュールとして読み込みます。読み込まれたモジュールは、ファイルが変更されるたびに自動的に再読み込みされます。

```julia
MyModule = @ingredients("my_exported_function.jl")
```
