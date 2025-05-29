```
initialize(::Type{<:DependentScalingModel}, data::IDFdata, d₀::Real)
```

データに適応したDependentScalingmodelのパラメータベクトルを初期化します。初期化は、周辺スケーリングモデルと相関構造のために独立して行われます。
