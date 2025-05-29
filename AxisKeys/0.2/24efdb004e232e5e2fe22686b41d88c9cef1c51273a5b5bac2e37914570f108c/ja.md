```
wrapdims(A, T, keyvecs...)
wrapdims(A, T; name=keyvec...)
```

これは、すべてのキーに型 `T` を適用します。たとえば、これらのパッケージを使用して、`UniqueVector` や `AcceleratedArray` としてラップし、高速な検索を実現します。
