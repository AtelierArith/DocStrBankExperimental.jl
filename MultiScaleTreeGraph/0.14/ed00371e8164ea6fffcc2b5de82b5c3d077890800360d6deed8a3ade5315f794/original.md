```
transform!(node::Node, args..., <keyword arguments>)
transform(node::Node, args..., <keyword arguments>)
```

Transform (mutate) an MTG (`node`) in place (`transform!`) or on a copy (`transform`) to add attributes specified by `args...`.

# Arguments

  * `node::Node`: An MTG node (*e.g.* the whole mtg returned by `read_mtg()`).
  * `args::Any`: the transformations (see details)
  * <keyword arguments>:

      * `scale = nothing`: The scale to filter-in (i.e. to keep). Usually a Tuple-alike of integers.
      * `symbol = nothing`: The symbol to filter-in. Usually a Tuple-alike of Strings.
      * `link = nothing`: The link with the previous node to filter-in. Usually a Tuple-alike of Char.
      * `filter_fun = nothing`: Any filtering function taking a node as input, e.g. [`isleaf`](@ref).
      * `ignore_nothing = false`: filter-out the nodes with `nothing` values for the given

    attributes used as inputs (apply only to the form :var_name => ...)

# Returns

`transform!`: Nothing, mutates the (sub-)tree in-place. `transform`: A mutated copy of `node`.

# Notes

Carefull, `transform` is much slower than `transform!` because it makes a copy of the whole MTG each time.

# Details

The interface of the function is inspired from the one used in [`DataFrames.jl`](https://dataframes.juliadata.org/stable/), but adapted to an MTG.

The `args...` provided can be of the following forms:

1. a `:var_name => :new_var_name` pair. This form is used to rename an attribute name
2. a `:var_name => function => :new_var_name` or

`[:var_name1, :var_name2...] => function => :new_var_name` pair. The variables are declared as a Symbol or a String (or a vector of), and they are passed as positional arguments to the function. The new attribute name is optional and is automatically generated if not provided by concatenating the source column name(s) and the function name if any.

3. a `function => :new_var_name` form that applies a function to a node and puts the results

in a new attribute. This form is usually applied when searching ancestors or descendants values.

4. a `function` form that applies a mutating function to a node, without expecting any output.

This form is adapted when using a function that already mutates the node, without the need to return anything, *e.g.* [`branching_order!`](@ref).

Carefull to the form you use! Form 2 expect a function that takes one or more node attributes (== variables) as inputs, while form 3 and 4 expect a function that takes a node.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# We can use transform to apply a function over all nodes (same as using [`traverse!`](@ref))
transform!(mtg,  node -> isleaf(node) ? println(node_id(x)," is a leaf") : nothing)
node_5 is a leaf
node_7 is a leaf

# We can compute a new variable based on another. For example to know if the value of the
# `:Length` attribute is provided or not, we can do:
transform!(mtg, :Length => isnothing)
# To check the values we first call [`get_attributes`](@ref) to know the new variable name:
get_attributes(mtg)
# And then we get the values using [`descendants`](@ref)
descendants(mtg, :Length_isnothing, self = true)
# Or DataFrame:
DataFrame(mtg, :Length_isnothing)

# We can also set the attribute name ourselves like so:
transform!(mtg, :Length => isnothing => :no_length)
descendants(mtg, :no_length, self = true)

# We can provide anonymous functions if we want to:
transform!(mtg, :Length => (x -> isnothing(x)) => :no_length)
descendants(mtg, :no_length, self = true)

# When a node does not have an attribute, it returns `nothing`. Most basic functions do not
# handle those very well, e.g.:
transform!(mtg, :Length => log)
# It does not work because some nodes have no value for `:Length`.
# To remove automatically the nodes with `nothing` values, use `ignore_nothing`:
transform!(mtg, :Length => log => :log_length, ignore_nothing = true)
descendants(mtg, :log_length, self = true)

# Or you could handle these manually in your function if you prefer:
transform!(mtg, :Length => (x -> x === nothing ? nothing : log(x)) => :log_length2)
descendants(mtg, :log_length2, self = true)

# Another way is to give a filtering function as an argument:
transform!(mtg, :Length => log => :log_length, filter_fun = x -> x[:Length] !== nothing)

# We can use more than one attribute as input to our function like so:
transform!(
    mtg,
    [:Width, :Length] => ((x, y) -> (x/2)^2 * π * y) => :volume,
    filter_fun = x -> x[:Length] !== nothing && x[:Width] !== nothing
)
descendants(mtg, :volume, self = true)

# Note that `filter_fun` filter the node, so we use the node[:attribute] notation here.

# We can also chain operations, and they will be executed sequentially so we can use variables
# computed on the instruction just before:
density = 0.6
transform!(
    mtg,
    [:Width, :Length] => ((x, y) -> (x/2)^2 * π * y) => :vol,
    :vol => (x -> x * density) => :biomass,
    filter_fun = x -> x[:Length] !== nothing && x[:Width] !== nothing
)
DataFrame(mtg, [:vol, :biomass])

# We can also rename a variable like so:
transform!(
    mtg,
    :biomass => :mass,
    filter_fun = x -> x[:Length] !== nothing && x[:Width] !== nothing
)
DataFrame(mtg, [:vol, :mass])

# Finally, we can use variables from ancestors/descendants using the `function => :new_var` form:
function get_mass_descendants(x)
    masses = descendants(x, :mass, ignore_nothing = true)
    if length(masses) == 0
        nothing
    else
        sum(masses)
    end
end

transform!(
    mtg,
    get_mass_descendants => :mass_beared
)
DataFrame(mtg, [:mass, :mass_beared])
```
