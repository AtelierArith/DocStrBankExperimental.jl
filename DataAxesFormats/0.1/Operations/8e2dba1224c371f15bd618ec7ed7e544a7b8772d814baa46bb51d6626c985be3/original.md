```
Fraction([; dtype::Type])
```

Element-wise operation that converts every element to its fraction out of the total. If the total is zero, all the fractions are also set to zero. This implicitly assumes (but does not enforce) that all the entry value(s) are positive.

For matrices, each entry becomes its fraction out of the total of the column it belongs to. For vectors, each entry becomes its fraction out of the total of the vector. For scalars, this operation makes no sense so fails with an error.

**Parameters**

`dtype` - The default output data type is the [`float_dtype_for`](@ref) of the input data type.
