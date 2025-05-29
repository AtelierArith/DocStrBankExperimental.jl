```
struct DafView(daf::DafReader) <: DafReader
```

任意の [`DafReader`](@ref) データの読み取り専用ラッパーであり、それを別の [`DafReadOnly`](@ref) として任意のビューとして公開します。これは通常手動で作成されるものではなく、代わりに [`viewer`](@ref) を呼び出します。
