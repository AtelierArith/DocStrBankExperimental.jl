```
raneftables(m::MixedModel; uscale = false)
```

ランダム効果の条件付き平均を、Tables.jlに準拠したテーブルの`NamedTuple`として返します。

!!! note
    APIの保証は、NamedTupleがTables.jlテーブルを含むことのみであり、各テーブルの具体的な型については保証されていません。

