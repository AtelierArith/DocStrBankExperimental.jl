```
random_state(Pure()|Mixed(), ::System, linkdims::Int)
random_state(Pure()|Mixed(), ::Int, ::AbstractSite, linkdims::Int)
random_state(Pure()|Mixed(), ::Vector{<:AbstractSite}, linkdims::Int)
random_state(Pure()|Mixed(), ::State, linkdims::Int)
```

指定されたリンク次元を持つランダム状態を返します。Stateが与えられた場合は、指定された状態をランダム化します。
