```
@properties T block
```

Syntactic sugar for custom `getproperty`, `setproperty!`, and `propertynames` methods. For any type `T` passed to `@properties` these methods will be rewritten from their default.

## Examples

The following syntax assigns property names to function calls.

```jldoctest properties
julia> using FieldProperties

julia> mutable struct MyType
           x::Int
       end

julia> @properties MyType begin
           xint(self) = getfield(self, :x)
           xint!(self, val) = setfield!(self, :x, val)
           hello(self) = "hello"
       end

julia> mt = MyType(1)
MyType(1)

julia> mt.xint
1

julia> mt.xint = 2
2

julia> mt.xint
2

julia> mt.hello
"hello"

julia> propertynames(mt)
(:xint, :hello)

julia> mt.x
ERROR: Property x not found
[...]
```

There are three things you should take away from this:

1. `getproperty`, `setproperty!`, and `propertynames` are completely overwritten here
2. Any property assignment that ends with `!` is used to assign a `setproperty!`
3. `MyType` not longer can access the `x` field via `mt.x` (because of the first point).

It can be somewhat tedious to write out every `getfield` and `setfield` method, so let's redo this using `=>` to assign fields

```jldoctest properties
julia> @properties MyType begin
           xint(self) => :x
           xint!(self, val) => :x
           hello(self) = "hello"
       end

julia> mt = MyType(1)
MyType(1)

julia> mt.xint
1

julia> mt.xint = 2
2

julia> mt.xint
2

julia> mt.hello
"hello"

julia> propertynames(mt)
(:xint, :hello)

julia> mt.x
ERROR: Property x not found
[...]
```

Sometimes we want to use a modular approach to constructing a type. The following example requires users to know where to find the `x1`, `x2`, and `x3` fields.

```jldoctest properties
julia> mutable struct PropList1
           x2::Int
       end

julia> mutable struct PropList2
           x3::Int
       end

julia> mutable struct MyProperties
           x1::Int
           l1::PropList1
           l2::PropList2
       end

julia> mp = MyProperties(1, PropList1(2), PropList2(3))
MyProperties(1, PropList1(2), PropList2(3))

julia> mp.x1
1

julia> mp.l1.x2  # obnoxious for users
2

julia> mp.l2.x3  # also obnoxious for users
3
```

The following syntax tells our property methods to search through nested fields.

```jldoctest properties
julia> @properties MyProperties begin
           x1(self) => :x1
           x1!(self, val) => :x1
           Any(self) => (:l1, :l2)
           Any!(self, val) => (:l1, :l2)
       end

julia> propertynames(mp)
(:x1, :x2, :x3)

julia> mp.x1
1

julia> mp.x2
2

julia> mp.x3
3
```

The last two methods (`Any(x)` and `Any!(x, val)`) tell the `getproperty` and `setproperty!` methods search the `l1` and `l2` fields for any property that isn't `:x1`.

The lowered code is:

```julia
julia> @macroexpand @properties MyProperties begin
                  x1(self) => :x1
                  x1!(self, val) => :x1
                  Any(self) => (:l1, :l2)
                  Any!(self, val) => (:l1, :l2)
              end
quote
    function Base.getproperty(self::MyProperties, p::Symbol)
        if p === :x1
            getfield(self, :x1)
        else
            if hasproperty(getfield(self, :l1), p)
                getproperty(getfield(self, :l1), p)
            else
                getproperty(getfield(self, :l2), p)
            end
        end
    end
    function Base.setproperty!(self::MyProperties, p::Symbol, val)
        if p === :x1
            setfield!(self, :x1, val)
        else
            if hasproperty(getfield(self, :l1), p)
                setproperty!(getfield(self, :l1), p, val)
            else
                setproperty!(getfield(self, :l2), p, val)
            end
        end
    end
    function Base.propertynames(self::MyProperties)
        (:x1, propertynames(getfield(self, :l1))..., propertynames(getfield(self, :l2))...)
    end
end
```

Note that the the `:l1` and `l2` fields are searched in the same order they are called inside the macro (e.g., `Any(x) => (:l1, :l2)` results in searching `:l1` then `:l2`).
