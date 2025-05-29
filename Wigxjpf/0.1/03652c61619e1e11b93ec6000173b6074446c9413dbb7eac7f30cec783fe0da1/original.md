```
wig_table_init(max_two_j::Integer, wigner_type::Integer)
```

Initialize the calculation table. Must be called before evaluating any Wigner symbols.

`max_two_j` is twice the highest absolute value of all `j` values to be evaluated.

`wigner_type` should be 3, 6, or 9. When multiple types are to be used, you should use the highest value for this parameter. 

> When used in a multi-threaded environment, this function should be called **globally**.

