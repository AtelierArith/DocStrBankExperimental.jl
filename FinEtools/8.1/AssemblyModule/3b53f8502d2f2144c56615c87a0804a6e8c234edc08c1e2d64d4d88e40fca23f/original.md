```
expectedntriples(
    a::A,
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
) where {A<:AbstractSysmatAssembler, IT}
```

How many triples (I, J, V) does the assembler expect to store?

Default is: the product of the size of the element matrices times the number of matrices. 
