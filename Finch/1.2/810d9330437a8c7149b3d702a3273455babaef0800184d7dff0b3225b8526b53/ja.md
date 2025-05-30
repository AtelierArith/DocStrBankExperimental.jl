```
PatternLevel{[Tp=Int]}()
```

パターンレベルのサブファイバーはブール値のtrueですが、その`fill_value`はfalseです。PatternLevelsは、他のファイバーによって保存される値を表すテンソルを作成するために使用されます。使用例については[`pattern!`](@ref)を参照してください。

```jldoctest
julia> tensor_tree(Tensor(Dense(Pattern()), 3))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: true
   ├─ [2]: true
   └─ [3]: true
```
