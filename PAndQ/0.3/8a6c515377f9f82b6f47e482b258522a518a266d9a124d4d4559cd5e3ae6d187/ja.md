```
fold(f, pairs...)
```

任意の数のネストされたフォールドと、各演算子の[`Associativity`](@ref Interface.Associativity)および[`initial_value`](@ref Interface.initial_value)を決定する特性を持つ`mapreduce`の一般化です。

関数`f`は、`pairs`の数だけのパラメータを受け入れなければなりません。各ペアは、最初の要素が二項演算子で、2番目の要素がフォールドされるイテラブルである2要素のイテラブルでなければなりません。

単一のペアを与えた場合、この関数は`mapreduce`やその他の類似の関数に似ています。追加のペアを与えることで、次のパターンを一般化します：

```julia
mapreduce(a, xs) do x
    mapreduce(b, ys) do y
        ...
    end
end
```

これは次のように書き換えることができます：

```julia
fold(a => xs, b => ys, ...) do x, y, ...
    ...
end
```

# 例

```jldoctest
julia> fold(⊤)
⊤

julia> @atomize fold(¬, (∧) => (p, q))
¬p ∧ ¬q

julia> @atomize fold(↔, (∧) => (p, q), (∨) => (r, s))
((p ↔ r) ∨ (p ↔ s)) ∧ ((q ↔ r) ∨ (q ↔ s))
```
