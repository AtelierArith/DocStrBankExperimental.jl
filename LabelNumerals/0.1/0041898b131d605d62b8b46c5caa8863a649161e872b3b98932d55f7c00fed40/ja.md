```
    LabelNumeral(s::String; prefix="", caselower=false) --> LabelNumeral{Int}
```

LabelNumeral{Int}型を返す特化したコンストラクタです。

例:

```
julia> a = LabelNumeral("23"; prefix="A-", caselower=true)
A-23
```

`prefix`は`caselower`パラメータの影響を受けません。
