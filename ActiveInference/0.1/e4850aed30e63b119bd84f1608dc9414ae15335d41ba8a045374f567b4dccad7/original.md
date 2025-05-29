```
create_matrix_templates(shapes::Vector{Vector{Int64}}, template_type::String)
```

Creates a multidimensional template based on the specified vector of shape vectors and template type. Templates can be uniform, random, or filled with zeros.

# Arguments

  * `shapes::Vector{Vector{Int64}}`: A vector of vectors, where each vector represent a dimension of the template to create.
  * `template_type::String`: The type of templates to create. Can be "uniform" (default), "random", or "zeros".

# Returns

  * A vector of arrays, each having the multi-dimensional shape specified in the input vector.
