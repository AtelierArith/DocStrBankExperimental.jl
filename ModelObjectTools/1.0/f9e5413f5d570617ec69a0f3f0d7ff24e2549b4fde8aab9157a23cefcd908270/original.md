showModelObject(mo)

Displays a representation of the model object mo that  is simple to understand and that can be used as a command to construct an identical object (if a default constructor is available).

# Examples

```julia-repl

julia> struct ExStr
       a::Float64
       vec::Tuple{Float64, Float64, Float64}
       end

julia> s = ExStr(3.0, (1.0,2.0,10.0))
ExStr(3.0, (1.0, 2.0, 10.0))

julia> showModelObject(s)
modelObjectFromAnother(ExStr(), 
                           :a => 3.0, 
                         :vec => (1.0, 2.0, 10.0))
```
