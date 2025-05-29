```
timesum(snoop::Vector{Tuple{Float64, Core.MethodInstance}}, unit = :s)
```

Calculates the total time measured by a snoop macro. `unit` can be :s or :ms.

# Examples

```julia
using SnoopCompile
data = @snoopi begin
    using MatLang
    MatLang_rootpath = dirname(dirname(pathof("MatLang")))

    include("$MatLang_rootpath/test/runtests.jl")
end
println(timesum(data, :ms))
```
