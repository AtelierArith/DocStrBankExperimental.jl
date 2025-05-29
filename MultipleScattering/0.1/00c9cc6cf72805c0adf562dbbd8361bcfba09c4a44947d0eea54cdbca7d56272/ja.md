```
RegularSource(medium::P, field::Function, coef::Function)
```

は、システム全体を駆動/強制するソースフィールドを記述する構造体型です。これは、入射波としても知られています。3つのフィールド `RegularSource.medium`、`RegularSource.field`、および `RegularSource.coef` を持っています。

位置 'x' と角周波数 'ω' におけるソースフィールドは次のように与えられます。

```julia-repl
x = [1.0,0.0]
ω = 1.0
RegularSource.field(x,ω)
```

フィールド `RegularSource.coef` は regular*basis*function(medium::Acoustic{T,2}, ω::T) です。
