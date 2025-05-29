```
open_dataset(parent::Union{File, Group}, path::AbstractString; properties...)
```

`parent`の下の`path`にある既存の[`HDF5.Dataset`](@ref)を開きます。

オプションのキーワード引数には、[`DatasetAccessProperties`](@ref)または[`DatasetTransferProperties`](@ref)に属する任意のキーワードが含まれます。
