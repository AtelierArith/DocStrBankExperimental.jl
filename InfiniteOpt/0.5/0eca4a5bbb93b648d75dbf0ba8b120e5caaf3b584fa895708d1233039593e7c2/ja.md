```
clear_optimizer_model_build!(model::InfiniteModel)::JuMP.Model
```

適切な `Base.empty!` の呼び出しを使用して最適化モデルを空にします。これにより、最適化者、属性、および空の最適化モデルデータ構造を維持したまま、`model.optimizer_model` が実質的にリセットされます。これは [`build_optimizer_model!`](@ref) によって使用される内部メソッドとして意図されています。
