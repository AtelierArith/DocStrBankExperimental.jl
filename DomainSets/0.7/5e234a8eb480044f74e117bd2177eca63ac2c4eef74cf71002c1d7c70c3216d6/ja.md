```
canonicaldomain([ctype::CanonicalType, ]d)
```

与えられたドメインの関連する標準ドメインを返します（存在する場合）。

たとえば、区間 `[a,b]` の標準ドメインは区間 `[-1,1]` です。

オプションで、標準タイプ引数は代替の標準ドメインを指定できます。標準ドメインは、ドメイン間の等価性を確立し、ドメイン間のマップを見つけ、パラメータ化を見つけるのに役立ちます。

ドメインが標準ドメインを実装している場合、`mapfrom_canonical` および `mapto_canonical` も実装する必要があります。

参照: [`mapfrom_canonical`](@ref), [`mapto_canonical`](@ref).
