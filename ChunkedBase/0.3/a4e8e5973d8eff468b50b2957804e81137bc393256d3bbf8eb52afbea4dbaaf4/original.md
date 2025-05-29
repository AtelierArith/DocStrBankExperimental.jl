```
AbstractParsingContext
```

Users should subtype this to create custom parsing contexts variables which are then used in `parse_file_parallel` / `parse_file_serial`, to dispatch on their `populate_result_buffer!` method.

# See also:

  * [`parse_file_parallel`](@ref), [`parse_file_serial`](@ref), [`populate_result_buffer!`](@ref)
