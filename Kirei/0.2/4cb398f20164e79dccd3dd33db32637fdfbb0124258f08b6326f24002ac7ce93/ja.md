```
@variadic_ccall [lib] cfunc(arg0::T0, arg1::T1; varargs...)::TR
```

`@generated` 関数で可変引数の C 関数を呼び出すために使用されます。

単純な型のみがサポートされています。

例:

```julia
@generated printf(fmt, varargs...) = @variadic_ccall printf(s::Cstring; varargs...)::Cint
```
