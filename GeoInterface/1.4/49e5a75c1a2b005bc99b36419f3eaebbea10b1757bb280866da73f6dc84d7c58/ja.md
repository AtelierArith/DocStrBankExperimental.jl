```
GeoInterface.isgeometry(x) => Bool
```

オブジェクト `x` がジオメトリであるかどうかを確認し、したがって暗黙的に GeoInterface メソッドをサポートしているかどうかを確認します。`MyType` を実装するユーザーには、`isgeometry(::Type{MyType})` のみを定義することをお勧めします。`isgeometry(::MyType)` は自動的にこのメソッドに委譲されます。
