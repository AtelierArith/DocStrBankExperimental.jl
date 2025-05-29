未知の変数を1つ以上定義します。

```julia
@variables t α σ(..) β[1:2]
@variables w(..) x(t) y z(t, α, x)

expr = β[1]* x + y^α + σ(3) * (z - t) - β[2] * w(t - 1)
```

`(..)`は値が呼び出されないことを示します。

Symbolicsは、あるサイズの配列を示す変数を作成することをサポートしています。

```jldoctest
julia> @variables x[1:3]
1-element Vector{Symbolics.Arr{Num, 1}}:
 x[1:3]

julia> @variables y[1:3, 1:6] # テンソルのサポート
1-element Vector{Symbolics.Arr{Num, 2}}:
 y[1:3,1:6]

julia> @variables t z(t)[1:3] # 依存変数にも対応
2-element Vector{Any}:
 t
  (z(t))[1:3]
```

配列を表すシンボルまたは式は、`scalarize`関数を使用してシンボルまたは式の配列に変換できます。

```jldoctest
julia> Symbolics.scalarize(z)
3-element Vector{Num}:
 (z(t))[1]
 (z(t))[2]
 (z(t))[3]
```

`@variables`は、定義されたすべての変数のベクターを返すことに注意してください。

`@variables`は、`$`補間演算子によってランタイムシンボル値を受け取ることもでき、この場合、`@variables`は自動的に値を割り当てず、代わりにシンボリック変数のベクターを返します。残りの構文もここで適用されます。

```jldoctest
julia> a, b, c = :runtime_symbol_value, :value_b, :value_c
(:runtime_symbol_value, :value_b, :value_c)

julia> vars = @variables t $a $b(t) $c(t)[1:3]
4-element Vector{Any}:
      t
 runtime_symbol_value
   value_b(t)
       (value_c(t))[1:3]

julia> (t, a, b, c)
(t, :runtime_symbol_value, :value_b, :value_c)
```
