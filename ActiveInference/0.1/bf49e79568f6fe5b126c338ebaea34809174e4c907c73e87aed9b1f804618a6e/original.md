```
create_matrix_templates(shapes::Vector{Int64}, template_type::String)
```

Creates templates based on the specified shapes vector and template type. Templates can be uniform, random, or filled with zeros.

# Arguments

  * `shapes::Vector{Int64}`: A vector specifying the dimensions of each template to create.
  * `template_type::String`: The type of templates to create. Can be "uniform" (default), "random", or "zeros".

# Returns

  * A vector of arrays, each corresponding to the shape given by the input vector.
