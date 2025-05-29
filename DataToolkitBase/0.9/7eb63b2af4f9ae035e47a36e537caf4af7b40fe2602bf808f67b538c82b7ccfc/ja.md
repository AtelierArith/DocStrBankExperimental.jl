```
typeify(qt::QualifiedType; mod::Module=Main)
```

`qt`を`mod`で利用可能な`Type`に変換します。これが不可能な場合は、代わりに`nothing`が返されます。
