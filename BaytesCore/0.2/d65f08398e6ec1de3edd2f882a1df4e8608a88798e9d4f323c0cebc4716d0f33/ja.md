```julia
mutable struct Updater
```

不変構造体に格納および更新できる更新情報を格納するための可変構造体。更新が必要かどうかのブール値を含みます。ここでは、UpdateBoolフィールドを具体的な型として格納および更新することはできないことに注意してください。

# フィールド

  * `current::Bool`: 更新を適用する必要があるかどうかのブール値
