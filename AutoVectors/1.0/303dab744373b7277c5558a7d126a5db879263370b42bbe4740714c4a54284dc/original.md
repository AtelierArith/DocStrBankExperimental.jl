```
AutoVector(def=0.0,mini::Integer=1,maxi::Integer=0,miniloc::Integer=0)
AutoVector(f::Function,mini::Integer=1,maxi::Integer=0,miniloc::Integer=0)
AutoVector(v::Vector,mini::Integer=1,maxi::Integer=0,miniloc::Integer=0)
```

Frequently you just use

```
v = AutoVector(), defaulting to Float64, size 0
```

or     v = AutoVector(0), defaulting to Int64, size 0

An AutoVector expands when written to outside its range. Reading outside its range  does not expand the range, and gives def.

Arguments:

def–default element, usually 0.0. Determines the type T of AutoVector{T}

mini and maxi give the index range of the created AutoVector (logical indices, not index in data vector)

miniloc is the location of mini-1 within the data vector, default 0 (data index)

You can initialize an AutoVector with the default, from a function, or by putting in a vector. Most functions and constructors deal with logical indices, Data indices refers to location within the data vector dat, which should not be something to worry about normally.
