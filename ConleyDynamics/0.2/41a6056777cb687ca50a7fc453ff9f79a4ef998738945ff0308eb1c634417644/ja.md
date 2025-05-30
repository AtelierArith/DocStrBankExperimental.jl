```
sc = simplicial_torsion_space(n::Int, p::Int)
```

1次元のトーションを持つ空間の三角形分割を作成します。

この関数は、次の整数ホモロジー群を持つ単体複体を返します：

  * 次元0では整数の群です。
  * 次元1では整数を`n`で割った剰余です。
  * 次元2では自明な群です。

言い換えれば、この単体複体は次元1に非自明なトーションを持っています。これは、すべての境界辺が反時計回りに向けられ、これらの辺がすべて同一視される`n`-角形の三角形分割です。パラメータ`p`は基礎となる体の特性を指定します。

# 例

```jldoctest
julia> println(homology(simplicial_torsion_space(6,2)))
[1, 1, 1]

julia> println(homology(simplicial_torsion_space(6,3)))
[1, 1, 1]

julia> println(homology(simplicial_torsion_space(6,5)))
[1, 0, 0]
```
