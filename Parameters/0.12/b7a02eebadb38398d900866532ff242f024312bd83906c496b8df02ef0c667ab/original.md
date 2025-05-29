This is a package I use to handle numerical-model parameters, thus the name. However, it should be useful otherwise too. It has two main features:

  * keyword type constructors with default values, and
  * unpacking and packing of composite types and dicts.

The macro `@with_kw` which decorates a type definition to allow default values and a keyword constructor:

```
julia> using Parameters

julia> @with_kw struct A
           a::Int = 6
           b::Float64 = -1.1
           c::UInt8
       end

julia> A(c=4)
A
  a: 6
  b: -1.1
  c: 4
```

Unpacking is done with `@unpack` (`@pack!` is similar):

```
struct B
    a
    b
    c
end
@unpack a, c = B(4,5,6)
# is equivalent to
BB = B(4,5,6)
a = BB.a
c = BB.c
```
