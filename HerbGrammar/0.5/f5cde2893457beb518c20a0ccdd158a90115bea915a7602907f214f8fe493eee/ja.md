```
log_probability(grammar::AbstractGrammar, index::Int)::Real
```

`index`での文法のルールの対数確率を返します。

!!! warning
    文法が確率的でない場合、警告が表示され、均一な確率が仮定されます。

