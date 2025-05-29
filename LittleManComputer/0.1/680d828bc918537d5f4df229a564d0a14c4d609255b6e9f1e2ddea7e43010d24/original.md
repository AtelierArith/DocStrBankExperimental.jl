```
symboltable(lines::AbstractArray{<:AbstractString})
```

Record address of labels used in code in a symbol table.  Return this as a dictionary.

```
symtable = symboltable("foobar.lmc")

# Get address of LOOP label
address = symtable["LOOP"]
```
