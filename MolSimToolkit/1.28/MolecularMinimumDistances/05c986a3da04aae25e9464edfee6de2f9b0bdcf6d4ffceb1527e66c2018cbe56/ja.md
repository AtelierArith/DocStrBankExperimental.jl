```
MinimumDistance{T}
```

最小距離のリストは、`Vector{MinimumDistance{T}}`型の配列に格納されています。このベクトルのインデックスは、元の配列における分子のインデックスに対応しています。

`MinimumDistance{T}`は、カットオフ内に距離があるかどうかを示すブールマーカー、互いに近い分子の原子のインデックス`i`と`j`、および入力ベクトルの座標と同じ型`T`の距離`d`の4つのフィールドを含むシンプルな構造体です。`MinimumDistance`要素の情報にアクセスする最良の方法は、ゲッタ関数`within_cutoff`、`distance`、`iatom`、および`jatom`を通じて行うことです。

## 例

```julia-repl
julia> md = MinimumDistance{Float32}(true, 2, 5, 1.f0)
MinimumDistance{Float32}(true, 2, 5, 1.0f0)

julia> iatom(md)
2

julia> jatom(md)
5

julia> distance(md)
1.0f0

julia> within_cutoff(md)
true
```
