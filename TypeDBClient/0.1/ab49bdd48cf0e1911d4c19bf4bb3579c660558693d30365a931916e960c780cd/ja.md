```
set_supertype(r::RemoteConcept{<: AbstractThingType,<: AbstractCoreTransaction},
    super_type::AbstractThingType)
```

ここでは、特定のThingTypeを他のThingTypeのスーパタイプとして設定する機会があります。AttributeTypeとEntityTypeのような異なるルートタイプの混合は許可されていません。
