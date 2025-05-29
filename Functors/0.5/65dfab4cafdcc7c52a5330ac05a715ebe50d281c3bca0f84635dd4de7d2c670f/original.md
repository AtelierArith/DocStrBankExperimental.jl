```
KeyPath(keys...)
```

A type for representing a path of keys to a value in a nested structure. Can be constructed with a sequence of keys, or by concatenating other `KeyPath`s. Keys can be of type `Symbol`, `String`, `Int`, or `CartesianIndex`.

For custom types, access through symbol keys is assumed to be done with `getproperty`. For consistency, the method `Base.propertynames` is used to get the viable property names.

For string, integer, and cartesian index keys, the access is done with `getindex` instead.

See also [`getkeypath`](@ref), [`haskeypath`](@ref).

# Examples

```jldoctest
julia> kp = KeyPath(:b, 3)
KeyPath(:b, 3)

julia> KeyPath(:a, kp, :c, 4) # construct mixing keys and keypaths
KeyPath(:a, :b, 3, :c, 4)

julia> struct T
           a
           b
       end

julia> function Base.getproperty(x::T, k::Symbol)
            if k in fieldnames(T)
                return getfield(x, k)
            elseif k === :ab
                return "ab"
            else        
                error()
            end
        end;

julia> Base.propertynames(::T) = (:a, :b, :ab);

julia> x = T(3, Dict(:c => 4, :d => 5));

julia> getkeypath(x, KeyPath(:ab)) # equivalent to x.ab
"ab"

julia> getkeypath(x, KeyPath(:b, :c)) # equivalent to (x.b)[:c]
4
```
