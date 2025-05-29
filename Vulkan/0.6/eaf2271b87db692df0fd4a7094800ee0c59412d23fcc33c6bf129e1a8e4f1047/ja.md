デバイスプロパティは、サポートされている場合にSPIR-V機能を有効にします。

```julia
struct PropertyCondition
```

  * `type::Symbol`: 条件に関連するプロパティ構造の名前。
  * `member::Symbol`: テストされるプロパティ構造のメンバー。
  * `core_version::Union{Nothing, VersionNumber}`: 必要なVulkan APIのコアバージョン（該当する場合）。
  * `extension::Union{Nothing, String}`: 必要な拡張（該当する場合）。
  * `is_bool::Bool`: テストするプロパティがブール値であるかどうか。そうでない場合は、ビットマスクのビットになります。
  * `bit::Union{Nothing, Symbol}`: プロパティがブール値でない場合にプロパティに含める必要があるビット列挙の名前。
