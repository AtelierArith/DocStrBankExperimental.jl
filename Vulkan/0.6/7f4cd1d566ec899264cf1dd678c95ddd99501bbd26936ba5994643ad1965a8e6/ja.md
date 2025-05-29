機能が有効と見なされるために満たす必要がある条件。

```julia
struct FeatureCondition
```

  * `type::Symbol`: 条件に関連する機能構造の名前。
  * `member::Symbol`: 機能を有効にするためにtrueに設定する必要がある構造のメンバー。
  * `core_version::Union{Nothing, VersionNumber}`: 構造に対応するコアバージョン（該当する場合）。
  * `extension::Union{Nothing, String}`: 該当する構造に必要な拡張（該当する場合）。
