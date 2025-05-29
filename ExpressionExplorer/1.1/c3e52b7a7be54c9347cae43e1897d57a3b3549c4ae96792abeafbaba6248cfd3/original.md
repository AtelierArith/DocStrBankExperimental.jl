For an expression like `function Base.sqrt(x::Int)::Int x; end`, it has the following fields:

  * `name::FunctionName`: the name, `[:Base, :sqrt]`
  * `signature_hash::UInt`: a `UInt` that is unique for the type signature of the method declaration, ignoring argument names. In the example, this is equals `hash(ExpressionExplorer.canonalize( :(Base.sqrt(x::Int)::Int) ))`, see [`canonalize`](@ref) for more details.
