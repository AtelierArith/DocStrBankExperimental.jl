```
quantumnumbers(I::Ion, level::String)
quantumnumbers(I::Ion, sublevel)
```

`I`のエネルギーレベルまたはサブレベルの量子数を`NamedTuple`として返します。第二引数がレベルの場合、`(:n, :i, :s, :l, :j, :f)`を返します。第二引数がサブレベルの場合、`(:n, :i, :s, :l, :j, :f, :m)`を返します。
