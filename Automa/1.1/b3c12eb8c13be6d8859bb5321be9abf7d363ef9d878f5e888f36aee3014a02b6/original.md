Struct used to store variable names used in generated code. Contained in a `CodeGenContext`. Create a custom `Variables` for your `CodeGenContext` if you want to customize the variables used in Automa codegen, typically if you have conflicting variables with the same name.

Automa generates code with the following variables, shown below with their default names:

  * `p::Int`: current position of data
  * `p_end::Int`: end position of data
  * `is_eof::Bool`: Whether `p_end` marks end file stream
  * `cs::Int`: current state
  * `data::Any`: input data
  * `mem::SizedMemory`: Memory wrapping `data`
  * `byte::UInt8`: current byte being read from `data`
  * `buffer::TranscodingStreams.Buffer`: (`generate_reader` only)

# Example

```julia
julia> ctx = CodeGenContext(vars=Variables(byte=:u8));

julia> ctx.vars.byte
:u8
```
