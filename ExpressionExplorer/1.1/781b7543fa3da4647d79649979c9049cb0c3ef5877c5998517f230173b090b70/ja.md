```julia
compute_usings_imports(ex)::UsingsImports
```

この式に含まれる `using Module.Z, SomethingElse` や `import Module` のようなサブ式のリストを取得します。
