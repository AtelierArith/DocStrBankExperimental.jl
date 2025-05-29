```
to_dict(x, option::ToDictOption) -> OrderedDict
```

オブジェクト `x` を指定された `ToDictOption` を持つ `OrderedDict` に変換します。

# 例

```julia
to_dict(x, TOMLStyle) # TOML 互換
to_dict(x, YAMLStyle) # YAML 互換
to_dict(x, JSONStyle) # JSON 互換
```
