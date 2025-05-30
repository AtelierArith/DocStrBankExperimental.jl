```
StartInvData <: AbstractInvData
```

投資データで、初期容量が `AbstractInvData` に指定されています。この構造は、フィールド **`initial::TimeProfile`** を追加した [`NoStartInvData`](@ref) に似ています。以下を参照してください。

# [`NoStartInvData`](@ref) に加えてのフィールド

  * **`initial::TimeProfile`** は、`TimeProfile` としての初期容量です。初期容量の引退は、減少する容量を通じて達成できます。
