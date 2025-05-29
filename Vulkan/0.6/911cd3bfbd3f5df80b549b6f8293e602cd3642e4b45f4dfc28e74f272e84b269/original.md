Exception type indicating that an API function returned a non-success code.

```julia
struct VulkanError <: Exception
```

  * `msg::String`
  * `code::Any`
