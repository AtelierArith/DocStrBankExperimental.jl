```
@layer [showtype] MyModel [trainable=(field1,...)]
```

This macro adds convenience functionality to a custom type to serve  as a neural network layer, as a module, or as an entire model.

The optional keyword `trainable` allows you to specify which fields of your model can be trained,  instead of assuming all `fieldnames(MyModel)` to trainable.  Note that it is never necessary to tell Flux to ignore non-array objects such as functions or sizes. This can be also be done by defining [`trainable(::MyModel)`](@ref Optimisers.trainable) for your type.

The macro also handles overloads of the 3-arg `show(::IO, ::MIME"text/plain", ::MyModel)` for pretty printing.  The optional argument `showtype` can take any of the following values:

  * `:expand` (default): This will expand the representation of container types like `Chain`,   while maintaining a compat representation of types like `Dense` containing only arrays.
  * `:noexpand`: This is to be used in case your type contains other layers but you want to keep the representation simple.
  * `:ignore`: To opt out of the pretty printing.

You probably still want to define 2-arg `show(::IO, ::MyModel)`, the macro does not touch this.

Note that re-running the macro with different options may not remove all methods, you will need to restart.

# Example

```jldoctest
julia> struct Trio; a; b; c end

julia> tri = Trio(Dense([1.1 2.2], [0.0], tanh), Dense(hcat(3.3), false), Dropout(0.4))
Trio(Dense(2 => 1, tanh), Dense(1 => 1; bias=false), Dropout(0.4))

julia> Flux.@layer Trio

julia> tri  # now the layer is printed like Chain
Trio(
  Dense(2 => 1, tanh),                  # 3 parameters
  Dense(1 => 1; bias=false),            # 1 parameters
  Dropout(0.4),
)                   # Total: 3 arrays, 4 parameters, 240 bytes.

julia> Flux.@layer :noexpand Trio trainable=(a,b)

julia> tri  # now the layer is printed compactly
Trio(Dense(2 => 1, tanh), Dense(1 => 1; bias=false), Dropout(0.4))  # 4 parameters

julia> opt_state = Flux.setup(Adam(), tri); # `c` is not in the optimizer state
```

The macro also adds methods to make using Flux with Enzyme easier.

  * `Duplicated(m::Layer)` allocates a copy for the gradient (initially zero).
  * This is made callable, `(m::Duplicated{<:Layer})(x...) = m.val(x...)`
  * Pretty printing for `show(io, mime, ::Duplicated{<:Layer})`
