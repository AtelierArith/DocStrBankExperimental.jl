```
add!(opsum::OpSum,
     op1::String, i1::Int)

add!(opsum::OpSum,
     coef::Number,
     op1::String, i1::Int)

add!(opsum::OpSum,
     op1::String, i1::Int,
     op2::String, i2::Int,
     ops...)

add!(opsum::OpSum,
     coef::Number,
     op1::String, i1::Int,
     op2::String, i2::Int,
     ops...)

+(opsum:OpSum, term::Tuple)
```

Add a single- or multi-site operator term to the OpSum `opsum`. Each operator is specified by a name (String) and a site number (Int). The second version accepts a real or complex coefficient.

The `+` operator version of this function accepts a tuple with entries either (String,Int,String,Int,...) or (Number,String,Int,String,Int,...) where these tuple values are the same as valid inputs to the `add!` function. For inputting a very large number of terms (tuples) to an OpSum, consider using the broadcasted operator `.+=` which avoids reallocating the OpSum after each addition.

# Examples

```julia
opsum = OpSum()

add!(opsum,"Sz",2,"Sz",3)

opsum += ("Sz",3,"Sz",4)

opsum += (0.5,"S+",4,"S-",5)

opsum .+= (0.5,"S+",5,"S-",6)
```
