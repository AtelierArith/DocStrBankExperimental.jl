```
to_dict(x; include_defaults=true, exclude_nothing=false) -> OrderedDict
```

オブジェクト `x` を `OrderedDict` に変換します。

# キーワード引数

  * `include_defaults`: デフォルト値を含めるかどうか、デフォルトは `true` です。
  * `exclude_nothing`: 値が `nothing` のフィールドを除外します。これは、両方が `true` の場合に `include_defaults` を上書きします。

# フォーマットの互換性

Julia から TOML/YAML/JSON などのフォーマットにオプション構造体をマッピングする際には、対処すべき微妙な意味的互換性があります。 [`TOMLStyle`](@ref)、[`YAMLStyle`](@ref)、[`JSONStyle`](@ref) として便利な事前定義された変換オプション定数を提供します。

!!! ヒント     `to_dict` はデフォルトと同じ値を持つフィールドをエクスポートしません。ほとんどの場合、これはデフォルトの動作であり、ユーザーは `include_defaults` を使用すべきではありません。ただし、`include_defaults` を `true` に変更することでこれを上書きできます。
