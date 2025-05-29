```
Species(element::Gas, Z::Int) -> Species
```

`Gas`と電荷状態から`Species`を構築します。また、次のように`(::Gas)(Z)`の便利なコンストラクタを使用することもできます。

```julia
julia> Xenon(0) == Species(Xenon, 0)
true
```
