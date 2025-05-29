```
getCanonicalType(t::CXType) -> CXType
getCanonicalType(t::CLType) -> CLType
```

CXTypeの標準型を返します。

Clangの型システムは、typedefと特定の型が表現されるすべての方法を明示的にモデル化しています。標準型は、すべての「糖衣」を取り除いた基礎型です。たとえば、'T'が'int'のtypedefである場合、'T'の標準型は'int'になります。libclangの[`clang_getCanonicalType`](@ref)のラッパーです。
