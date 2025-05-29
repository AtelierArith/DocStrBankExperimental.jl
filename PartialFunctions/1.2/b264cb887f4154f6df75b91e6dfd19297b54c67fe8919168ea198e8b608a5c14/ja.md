```
($)(f::Function, args...)
```

指定された引数を f に部分的に適用します。通常は中置 `f $ args` として使用されます。

返される関数の型は [`PartialFunctions.PartialFunction{nothing, nothing, typeof(f), typeof(args)}`](@ref) です。

# 例

```jldoctest
julia> using PartialFunctions

julia> simonsays = println $ "Simon says: "
println("Simon says: ", ...)

julia> simonsays("Partial function application is cool!")
Simon says: Partial function application is cool!
```
