```
InteractionTransformer
```

A model type for constructing a interaction transformer, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
InteractionTransformer = @load InteractionTransformer pkg=MLJModels
```

Do `model = InteractionTransformer()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `InteractionTransformer(order=...)`.

Generates all polynomial interaction terms up to the given order for the subset of chosen columns.  Any column that contains elements with scitype `<:Infinite` is a valid basis to generate interactions.  If `features` is not specified, all such columns with scitype `<:Infinite` in the table are used as a basis.

In MLJ or MLJBase, you can transform features `X` with the single call

```
transform(machine(model), X)
```

See also the example below.

# Hyper-parameters

  * `order`: Maximum order of interactions to be generated.
  * `features`: Restricts interations generation to those columns

# Operations

  * `transform(machine(model), X)`: Generates polynomial interaction terms out of table `X` using the hyper-parameters specified in `model`.

# Example

```
using MLJ

X = (
    A = [1, 2, 3],
    B = [4, 5, 6],
    C = [7, 8, 9],
    D = ["x₁", "x₂", "x₃"]
)
it = InteractionTransformer(order=3)
mach = machine(it)

julia> transform(mach, X)
(A = [1, 2, 3],
 B = [4, 5, 6],
 C = [7, 8, 9],
 D = ["x₁", "x₂", "x₃"],
 A_B = [4, 10, 18],
 A_C = [7, 16, 27],
 B_C = [28, 40, 54],
 A_B_C = [28, 80, 162],)

it = InteractionTransformer(order=2, features=[:A, :B])
mach = machine(it)

julia> transform(mach, X)
(A = [1, 2, 3],
 B = [4, 5, 6],
 C = [7, 8, 9],
 D = ["x₁", "x₂", "x₃"],
 A_B = [4, 10, 18],)

```
