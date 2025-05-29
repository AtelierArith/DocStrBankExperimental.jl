```
LatticeRule32(z, s, n)
LatticeRule32(z, s)
LatticeRule32(z)
```

`s`次元の生成ベクトル`z`を持つランク1ラティスルールを、最大で`n`点まで返します。

最大点数`n`が指定されていない場合、`n = typemax(UInt32) = 2^32 - 1`と仮定します。次元数`s`が指定されていない場合、`s = length(z)`と仮定します。

!!! info
    技術的には、`k`-th点がグレイコード化された根逆関数を使用して変換される拡張可能なラティスシーケンスを返します。これにより、既に計算された点を変更することなく、ラティスに点を追加することができます。


より多くの生成ベクトルはオンラインで[こちら](https://web.maths.unsw.edu.au/~fkuo/lattice/index.html)または[こちら](https://people.cs.kuleuven.be/~dirk.nuyens/qmc-generators/)で見つけることができます。

# 例

```jldoctest; setup = :(using LatticeRules; import Random; Random.seed!(1))
julia> lattice_rule = LatticeRule32([UInt32(1), UInt32(5)], 2, 8) # フィボナッチラティス
LatticeRule32{2}

julia> getpoint(lattice_rule, 2)
2-element Array{Float64,1}:
 0.25
 0.25

```

参照: [`getpoint`](@ref), [`ShiftedLatticeRule32`](@ref) ```
