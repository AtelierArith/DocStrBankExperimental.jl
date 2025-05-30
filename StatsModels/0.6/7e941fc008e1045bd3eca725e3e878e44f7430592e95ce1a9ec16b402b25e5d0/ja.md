```
setcontrasts!(mf::ModelFrame; kwargs...)
setcontrasts!(mf::ModelFrame, contrasts::Dict{Symbol})
```

[`ModelFrame`](@ref)内のカテゴリ変数のコーディングに使用されるコントラストをインプレースで更新します。これは、提供されたコントラストと`ModelFrame`のデータに基づいて新しいスキーマを計算し、それを`ModelFrame`の`FormulaTerm`に適用することによって実現されます。

注意すべきは、`ModelFrame`自体のみが変更されることです：`AbstractTerm`は不変であるため、変更が行われるとコピーが生成されます。
