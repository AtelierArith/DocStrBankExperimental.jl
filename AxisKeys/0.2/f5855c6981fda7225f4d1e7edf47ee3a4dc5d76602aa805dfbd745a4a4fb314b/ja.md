```
Index[i]
```

これは、`A(:b, Near(3.14), Index[4:5], "f")`のように角括弧インデックスを混ぜることを可能にするために存在します。また、`Index[end]`と書くこともできますが、まだ`Index[end-2]`はできません。

```
Key(val)
```

これは、インデックス内でのルックアップを実行するために存在し、`A[Key(:b), Near(3.14), 4:5, Key("f")]`を可能にします。

`Key(isequal(:b))`と書くことは、単に`isequal(:b)`と同等であり、すべての一致を見つけますが、`Key(:b)`は最初のものだけを見つけ（次元を落とします）。

# 例

```jldoctest
julia> v = KeyedArray(Symbol.('a':'e'), 10:10:50)
1次元の KeyedArray(...) キー付き:
↓   5要素の StepRange{Int64,...}
およびデータ、5要素の Vector{Symbol}:
 (10)  :a
 (20)  :b
 (30)  :c
 (40)  :d
 (50)  :e

julia> v[Key(30)] == v(30) == v(Index[3]) == v[3]
true

julia> v[==(30)] == v(Index[3:3]) == v[3:3]
true
```
