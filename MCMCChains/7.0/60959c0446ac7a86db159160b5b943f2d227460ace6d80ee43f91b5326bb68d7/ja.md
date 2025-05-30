```
setinfo(c::Chains, n::NamedTuple)
```

`info` フィールドに `NamedTuple` 型 `n` を配置した新しい `Chains` オブジェクトを返します。

# 例

```julia
new_chn = setinfo(chn, NamedTuple{(:a, :b)}((1, 2)))
```
