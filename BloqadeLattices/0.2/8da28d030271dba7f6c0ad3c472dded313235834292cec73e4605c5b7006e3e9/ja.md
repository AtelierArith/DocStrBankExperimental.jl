```
struct RectangularLattice <: AbstractLattice{2}
```

2D長方形格子を表す型。

[`generate_sites`](@ref)関数の引数として使用され、追加の引数でサイトの繰り返し回数を指定して長方形パターンのタイルを生成します。長方形は2D格子であるため、追加の入力として2つの整数引数が必要です。この型は、アスペクト比として単一の整数を渡すことにより、ブレヴァイ格子ベクトルの1つの長さを変更することも可能にします。

# 例

```julia-repl
julia> generate_sites(RectangularLattice(2.0), 2, 2)
4-element AtomList{2, Float64}:
 (0.0, 0.0)
 (1.0, 0.0)
 (0.0, 2.0)
 (1.0, 2.0)
```

格子ベクトルとサイトを返すオーバーライドされた関数は、[`lattice_vectors(::RectangularLattice)`](@ref)および[`lattice_sites(::RectangularLattice)`](@ref)として存在します。
