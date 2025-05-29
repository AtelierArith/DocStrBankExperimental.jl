```
checkantecedent(
    m::Union{Rule,Branch},
    args...;
    kwargs...
)
    check(antecedent(m), args...; kwargs...)
end
```

ルールの前提をインスタンスまたはデータセットで単純にチェックします。

関連情報としては [`antecedent`](@ref), [`Rule`](@ref), [`Branch`](@ref) があります。
