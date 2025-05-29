```julia
begin_supplemental_attributes_update(
    func::Function,
    sys::PowerSystems.System
) -> Any

```

補足属性の更新を開始します。パフォーマンスを向上させるために、多くの補足属性を追加または削除する際にこの関数を使用してください。

更新中にエラーが発生した場合、変更は元に戻されます。

# 例

```julia
begin_supplemental_attributes_update(sys) do
    add_supplemental_attribute!(sys, component1, attribute1)
    add_supplemental_attribute!(sys, component2, attribute2)
end
```
