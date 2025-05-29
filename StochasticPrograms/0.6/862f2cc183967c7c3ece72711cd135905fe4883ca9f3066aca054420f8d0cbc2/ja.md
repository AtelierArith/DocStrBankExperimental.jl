```
decision_by_name(stochasticprogram::Stochasticprogram,
                 stage::Integer,
                 name::String)::Union{AbstractVariableRef, Nothing}
```

`stochasticprogram`の`stage`で`name`属性を持つ変数の参照を返します。もしこの名前属性を持つ変数が存在しない場合は`Nothing`を返します。ステージ`s`で`name`が名前属性として複数の変数に存在する場合はエラーをスローします。
