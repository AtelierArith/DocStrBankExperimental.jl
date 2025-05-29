```
support_label(method::GenerativeDerivativeMethod)
```

Return the support label associated with `method` if there is one, errors otherwise.  This depends on [`generative_support_info`](@ref generative_support_info(::AbstractDerivativeMethod))  being defined for the type of `method`.
