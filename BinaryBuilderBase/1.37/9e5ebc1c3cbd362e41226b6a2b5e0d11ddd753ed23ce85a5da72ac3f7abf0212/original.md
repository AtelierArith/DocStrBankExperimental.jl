A `Product` is an expected result after building or installation of a package.

Examples of `Product`s include [`LibraryProduct`](@ref), [`FrameworkProduct`](@ref), [`ExecutableProduct`](@ref) and [`FileProduct`](@ref). All `Product` types must define the following minimum set of functionality:

  * [`locate(::Product)`](@ref): given a `Product`, locate it within the wrapped `Prefix` returning its location as a string
  * [`satisfied(::Product)`](@ref): given a `Product`, determine whether it has been successfully satisfied (e.g. it is locateable and it passes all callbacks)
  * [`variable_name(::Product)`](@ref): return the variable name assigned to a `Product`
  * `repr(::Product)`: Return a representation of this `Product`, useful for auto-generating source code that constructs `Products`, if that's your thing.
