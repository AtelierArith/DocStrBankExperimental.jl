```
signature(::Type{AbstractSignature}, object, timestamp, data) -> String
```

与えられた `object`、`timestamp`、および `data` の検証可能なチェックサムを計算します。

必要な暗号ライブラリを持ち込むパッケージによって拡張されます。`signature` の拡張者は、自分のメソッドシグネチャで使用するために `AbstractSignature` の独自のサブタイプを定義する必要があります。

# 例

```julia
struct MySignature <: AbstractSignature
    # ...
end

signature(::Type{MySignature}, object, timestamp, data) = # ...
```

`signature` とともに、拡張者は新しいタイプで動作するように `is_signed` と `verify` も拡張する必要があります。
