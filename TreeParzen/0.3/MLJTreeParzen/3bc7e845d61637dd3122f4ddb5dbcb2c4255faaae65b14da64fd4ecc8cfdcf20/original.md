```julia
struct MLJTreeParzenSpace
```

Data structure to store the user selected search space plus any user-provided suggestions. There are multiple constructors to support a variety of use cases.

  * `space::Dict{Symbol}`: The user's space as a dictionary of parameter names and (potentially nested) `TreeParzen.HP.*` expressions

  * `suggestions::Vector{Dict{Symbol}}`: The set of fixed points suggested provided to search. The number of random warn-up rounds is reduced by the amount of suggestions provided
