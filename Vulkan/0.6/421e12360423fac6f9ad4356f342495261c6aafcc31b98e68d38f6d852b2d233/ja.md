`next` チェーンで全ての引数を連結して、新しい構造 `next` チェーンを形成します。

もし `nexts` が空であれば、`C_NULL` が返されます。

```julia
chain(nexts::Vulkan.HighLevelStruct...) -> Any

```
