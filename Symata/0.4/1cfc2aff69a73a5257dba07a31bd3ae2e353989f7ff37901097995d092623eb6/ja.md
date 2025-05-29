```
symparsestring(s::String)::Vector{Any}
```

`s`をSymata式の配列に解析します。配列の各要素には1つの式が含まれます。

Symata式は評価されません。例えば、`symparsestring("b + b")`はSymata式`Plus(b, b)`を返し、`Times(2, b)`は返しません。

*Symata式*というフレーズには、数値、シンボルなどが含まれることに注意してください。

`symparseeval`を参照してください。
