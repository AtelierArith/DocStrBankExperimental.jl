```
struct MultiFormula{F<:Formula} <: AbstractSyntaxStructure
    modforms::Dict{Int,F}
end
```

`MultiLogiset`でチェックできる象徴的前提で、前提をモダリティに関連付けます。
