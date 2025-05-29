```julia
add_dyn_injectors!(
    sys::PowerSystems.System,
    dyr_file::AbstractString
)

```

すでに作成されたシステムに動的コンポーネントを追加します。システムはすでに .raw ファイルから解析されている必要があります。

# 例:

```julia
dyr_file = "Example.dyr"
add_dyn_injectors!(sys, dyr_file)
```
