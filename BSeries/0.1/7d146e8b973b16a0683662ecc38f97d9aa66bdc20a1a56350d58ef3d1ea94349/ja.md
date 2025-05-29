```
AverageVectorFieldMethod([T=Rational{Int}])
```

平均ベクトル場（AVF）法の表現を、型 `T` の係数を使用して構築します。これを引数として [`bseries`](@ref) に渡すことで、対応するB系列を構築できます。

# 例

次のように生成できます。

```jldoctest
julia> series = bseries(AverageVectorFieldMethod(), 3)
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 5 entries:
  RootedTree{Int64}: Int64[]   => 1
  RootedTree{Int64}: [1]       => 1
  RootedTree{Int64}: [1, 2]    => 1//2
  RootedTree{Int64}: [1, 2, 3] => 1//4
  RootedTree{Int64}: [1, 2, 2] => 1//3
```

# 参考文献

平均ベクトル場（AVF）法のB系列は、$b(.) = 1$ および $b([t_1, ..., t_n]) = b(t_1)...b(t_n) / (n + 1)$ で与えられます。詳細は以下を参照してください。

  * Elena Celledoni, Robert I. McLachlan, David I. McLaren, Brynjulf Owren, G. Reinout W. Quispel, and William M. Wright. "エネルギー保存型ルンゲ・クッタ法." ESAIM: 数理モデルと数値解析 43, no. 4 (2009): 645-649. [DOI: 10.1051/m2an/2009020](https://doi.org/10.1051/m2an/2009020)
