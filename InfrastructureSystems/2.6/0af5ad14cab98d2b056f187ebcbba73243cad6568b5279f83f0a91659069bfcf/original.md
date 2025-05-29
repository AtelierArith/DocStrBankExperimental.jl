Factory function to create the appropriate subtype of [`ComponentSelector`](@ref) given the arguments. Users should call this rather than manually constructing `ComponentSelector`s.

# Arguments

Several methods of this function have a parameter `groupby::Union{Symbol, Function}`, which specifies how the selector is grouped for the purposes of `get_groups`. The `groupby` argument has the following semantics:

  * `groupby = :each` (default): each component that makes up the selector forms its own group. The number of groups from `get_groups` will be equal to the number of components from `get_components`.
  * `groupby = :all`: all components that make up the selector are put into the same group. `get_groups` will yield one group.
  * `groupby = partition_function`: if the argument is a user-supplied function, the function will be applied to each component; all components with the same result under the function will be grouped together, with the name of the group specified by the function's output.

Other arguments are documented on a per-method basis.

# Examples

See the methods.
