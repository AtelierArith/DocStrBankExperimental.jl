```
to_sized(sys::AbstractStateSpace)
```

[`HeteroStateSpace`](@ref)を返します。ここで、システム行列はSizedMatrix型です。

*注意: この関数は根本的に型が不安定です。* 最大のパフォーマンスを得るためには、サイズ付きシステムを手動で作成するか、関数バリア技術を利用してください。
