```
abstract type PipeMode <: TransmissionMode
```

追加の変数ポテンシャルのための `TransmissionMode` モード。

`PipeMode` はデフォルトで一方向です。双方向パイプラインを含める予定がある場合は、関数 [`is_bidirectional`](@ref) に新しいメソッドを提供する必要があります。
