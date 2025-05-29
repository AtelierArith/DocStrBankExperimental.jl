```
meq(exp)
```

Macro to expand functions like `t[d1 in dim1, d2 in dim2, dfix,..] = value`

With this macro it is possible to write:

```
@meq par1[d1 in DIM1, d2 in DIM2, dfix3] =  par2[d1,d2]+par3[d1,d2]
```

and obtain

```
[par1[d1,d2,dfix3] =  par2[d1,d2]+par3[d1,d2] for d1 in DIM1, d2 in DIM2]
```

That is, it is possible to write "model equations" in a concise and readable way.
