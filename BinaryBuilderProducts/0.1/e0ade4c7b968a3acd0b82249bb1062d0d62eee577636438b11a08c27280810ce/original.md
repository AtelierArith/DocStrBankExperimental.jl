An `AbstractProduct` is an expected result after building of a package.

Examples of `Product`s include [`LibraryProduct`](@ref), [`FrameworkProduct`](@ref), [`ExecutableProduct`](@ref) and [`FileProduct`](@ref). All `AbstractProduct` types must define the following minimum set of functionality:

  * [`locate(product::AbstractProduct, prefix::String; env::Dict)`](@ref) Locate a product relative to the given `prefix`, returning its location as a string. Templating of environment variables is performed with the given `env` dictionary. Returns `nothing` if location fails.
  * [`variable_name(::AbstractProduct)`](@ref): Returns the given variable name for a product as a `Symbol`.
