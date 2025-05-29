```julia
getVariableType(_)

```

変数ノード `variableType` は、その因子グラフのノードに格納されている変数の型に関連するさまざまなメタデータを保持しています。

ノート

  * この関数は `::Type{<:InferenceVariable}` ではなく `::T` のインスタンスを返すというAPIの特異性があります。

DevWork

  * TODO, IncrementalInference.jl 1228を参照

関連

getVariableType
