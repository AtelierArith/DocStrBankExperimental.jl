Condition that a feature needs to satisfy to be considered enabled.

```julia
struct FeatureCondition
```

  * `type::Symbol`: Name of the feature structure relevant to the condition.
  * `member::Symbol`: Member of the structure which must be set to true to enable the feature.
  * `core_version::Union{Nothing, VersionNumber}`: Core version corresponding to the structure, if any.
  * `extension::Union{Nothing, String}`: Extension required for the corresponding structure, if any.
