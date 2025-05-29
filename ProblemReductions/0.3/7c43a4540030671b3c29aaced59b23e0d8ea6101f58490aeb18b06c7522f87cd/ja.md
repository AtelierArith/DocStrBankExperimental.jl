```
flavor_names(::Type{<:AbstractProblem}) -> Vector
```

自由度のフレーバー（ドメイン）の名前としてベクターを返します。メソッドが定義されていない場合は、[`flavors`](@ref)にフォールバックします。名前と構成の間で変換するには、`ProblemReductions.name2config`と`ProblemReductions.config2name`を使用してください。
