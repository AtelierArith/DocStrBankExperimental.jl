```
call_abi(p::AbstractPlatform)
```

指定された `Platform` オブジェクトの呼び出し ABI を `String` として取得します。明示的な `call_abi` 選択肢がないプラットフォーム（ほとんどのプラットフォーム）では `nothing` を返します。

# 例

```jldoctest
julia> call_abi(Platform("armv7l", "Linux"))
"eabihf"

julia> call_abi(Platform("x86_64", "macos"))
```
