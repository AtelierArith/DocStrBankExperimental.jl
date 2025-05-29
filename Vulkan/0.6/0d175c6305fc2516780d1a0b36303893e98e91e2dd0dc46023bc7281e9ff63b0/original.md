```
@check vkCreateInstance(args...)
```

Assign the expression to a variable named `_return_code`. Then, if the value is not a success code, return a [`VulkanError`](@ref) holding the return code.
