```
function ODESystem(sys::SDESystem)
```

`SDESystem`をノイズ方程式の代わりに`@brownian`変数を使用して同等の`ODESystem`に変換します。返されるシステムは`iscomplete`ではなく、`iscomplete(sys)`に関わらずインデックスキャッシュも持ちません。
