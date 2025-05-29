```
StaticStateSpace(sys::AbstractStateSpace)
```

型 SMatrix のシステム行列を持つ [`HeteroStateSpace`](@ref) を返します。

*注意: この関数は根本的に型が不安定です。* 最大のパフォーマンスを得るためには、静的システムを手動で作成するか、関数バリア技術を利用してください。
