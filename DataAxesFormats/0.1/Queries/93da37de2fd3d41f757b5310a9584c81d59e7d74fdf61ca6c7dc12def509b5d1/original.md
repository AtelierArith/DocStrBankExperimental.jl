```
full_vector_query(
    axis_query::Query,
    vector_query::QueryString,
    vector_name::Maybe{AbstractString} = nothing,
)::Query
```

Given a query for an axis, and some suffix query for a vector property, combine them into a full query for the vector values for the axis. This is used by [`FrameColumn`](@ref) for [`get_frame`](@ref) and also for queries of vector data in views.
