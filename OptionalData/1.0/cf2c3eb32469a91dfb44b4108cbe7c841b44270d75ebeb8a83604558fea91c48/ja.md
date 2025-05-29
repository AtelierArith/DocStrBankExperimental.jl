```
@OptionalData name type msg=""
```

定数 `name` を型 `OptData{type}` で初期化します。データがプッシュされる前に `name` にアクセスすると、カスタムエラーメッセージ `msg` を持つ例外がスローされます。

# 例

```julia
@OptionalData OPT_FLOAT Float64
```
