```
oncol(iname₁ => spec₁, ..., inameₙ => specₙ) -> f::Function
oncol(; $iname₁ = spec₁, ..., $inameₙ = specₙ) -> f::Function
```

列に作用する関数を組み合わせて、全行に作用する関数を作成します。

これは、`specᵢ` が還元ステップ関数または還元ステップ関数と出力列名の `Pair` のいずれかであるテーブル行に作用する還元ステップ関数を構築します。

また、`specᵢ` が単項関数または単項関数と出力列名の `Pair` のいずれかである場合に単項関数を定義します。

この関数は、DataFrames.jl の「`Pair` 表記」に触発されています（詳細は [Split-apply-combine · DataFrames.jl](https://juliadata.github.io/DataFrames.jl/stable/man/split_apply_combine/) および [`DataFrames.select`](https://juliadata.github.io/DataFrames.jl/stable/lib/functions/#DataFrames.select) を参照してください）。

# 例

```jldoctest oncol
julia> using DataTools
       using Transducers

julia> rf = oncol(a = +, b = *);

julia> foldl(rf, Map(identity), [(a = 1, b = 2), (a = 3, b = 4)])
(a = 4, b = 8)

julia> rf((a = 1, b = 2), (a = 3, b = 4))
(a = 4, b = 8)

julia> rf = oncol(:a => (+) => :sum, :a => max => :max);

julia> foldl(rf, Map(identity), [(a = 1,), (a = 2,)])
(sum = 3, max = 2)

julia> rf((sum = 1, max = 1), (a = 2,))
(sum = 3, max = 2)

julia> rf = oncol(:a => min, :a => max);

julia> foldl(rf, Map(identity), [(a = 2,), (a = 1,)])
(a_min = 1, a_max = 2)

julia> rf((a_min = 2, a_max = 2), (a = 1,))
(a_min = 1, a_max = 2)

julia> foldl(rf, Map(x -> (a = x,)), [5, 2, 6, 8, 3])
(a_min = 2, a_max = 8)
```

`oncol` は単項関数も定義します

```jldoctest oncol
julia> f = oncol(a = string);

julia> f((a = 1, b = 2))
(a = "1",)
```

`oncol` は入力関数の引数の数を検証しないことに注意してください。入力関数に単項および二項メソッドがある場合、`oncol` は両方の引数の数で呼び出すことができます：

```jldoctest oncol
julia> f((a = 1, b = 2), (a = 3, b = 4))
(a = "13",)
```
