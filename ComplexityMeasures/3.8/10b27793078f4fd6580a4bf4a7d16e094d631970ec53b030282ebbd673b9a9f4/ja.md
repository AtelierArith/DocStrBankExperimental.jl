```
codify(o::OutcomeSpace, x::Vector) → s::Vector{Int}
```

結果空間 `o` に従って `x` を符号化します。

## 説明

この関数が存在する理由は、常に入力 `x` 全体を一度に [`encode`](@ref) したいわけではないからです。時には、最初に `x` に何らかの変換を適用し、その後に変換された空間で [`Encoding`](@ref) を点ごとに適用することが望ましい場合があります。（[`OutcomeSpace`](@ref) がこの変換を指示します。）これは時系列データの符号化に役立ちます。

返される `s` の長さは [`OutcomeSpace`](@ref) に依存します。いくつかの結果空間は入力データの長さを保持します（例：[`UniqueElements`](@ref)）、一方で他の結果空間（例：[`OrdinalPatterns`](@ref)）は符号化の前に遅延埋め込みを行うため、`length(s) < length(x)` となることがあります。
