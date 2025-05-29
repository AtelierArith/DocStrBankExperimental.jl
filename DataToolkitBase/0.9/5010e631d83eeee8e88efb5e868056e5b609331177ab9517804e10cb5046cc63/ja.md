```
@addpkg name::Symbol uuid::String
```

`name` で識別されるパッケージを UUID `uuid` で登録します。このパッケージは `@import $name` で使用できるようになります。

すべての @addpkg ステートメントはモジュールの `__init__` 関数内に配置する必要があります。

# 例

```
@addpkg CSV "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
```
