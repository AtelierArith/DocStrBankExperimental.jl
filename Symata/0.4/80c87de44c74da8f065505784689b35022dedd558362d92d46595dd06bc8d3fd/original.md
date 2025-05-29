```
mxpra(head, args::MxprArgs)
```

Create a Symata expression with head `head` and arguments `args`. The arguments are not copied. An object of type `Mxpr{head}` is returned if `head` is a symbol, and of type `Mxpr{GenHead}` otherwise. The type `MxprArgs` is currently an alias for `Array{Any,1}` and can be instantiated with the function `newargs()`.
