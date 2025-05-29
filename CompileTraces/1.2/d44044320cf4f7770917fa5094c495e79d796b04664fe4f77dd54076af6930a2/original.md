Compile traces by calling [`compile_traces`](@ref) with `@__MODULE__` as first argument. See the documentation of [`compile_traces`](@ref) for more information.

Non-absolute literal strings for trace file paths will be expanded relative to the directory of the source location.

Keyword arguments can be parsed in any order in the form `name = value`.
