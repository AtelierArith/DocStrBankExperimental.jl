API関数が成功以外のコードを返したことを示す例外タイプ。

```julia
struct VulkanError <: Exception
```

  * `msg::String`
  * `code::Any`
