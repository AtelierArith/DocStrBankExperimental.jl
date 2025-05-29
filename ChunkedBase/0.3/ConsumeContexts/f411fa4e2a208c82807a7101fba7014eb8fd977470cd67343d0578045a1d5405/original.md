```
AbstractConsumeContext
```

End users should subtype this to create custom consume contexts which are then used in `parse_file_parallel` and `parse_file_serial`, to dispatch on their `populate_result_buffer!` method.

# See also:

  * [`parse_file_parallel`](@ref), [`parse_file_serial`](@ref), [`populate_result_buffer!`](@ref)
  * See also [`consume!`](@ref), [`setup_tasks!`](@ref), [`setup_tasks!`](@ref), [`cleanup`](@ref), [`AbstractResultBuffer`](@ref)
