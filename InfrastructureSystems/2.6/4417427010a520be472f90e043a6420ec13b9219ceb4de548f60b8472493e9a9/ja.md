```julia
get_name(
    selector::InfrastructureSystems.ComponentSelector
) -> Any

```

[`ComponentSelector`](@ref)の名前を取得します。これは、作成時に渡されたユーザー指定の名前か、セレクタの仕様から自動的に生成された名前のいずれかです。

# 例

```julia
sel = make_selector(RenewableDispatch)
get_name(sel)  # "RenewableDispatch"
```
