```
unwind(iterators...)
```

`iterators`によって生成されるすべての可能な値の組み合わせを行列`A`の行として表現します。より詳しく言うと、`A`は`iterators`内の各イテレータに対して1列を持ち、イテレータによって取られる異なる可能な値の組み合わせごとに1行を持ちます。最初の列の要素は最も速くサイクルし、最後の列の要素は最も遅くサイクルします。

### 例

```julia-repl
julia> iterators = ([1, 2], ["a","b"], ["x", "y", "z"]);
julia> MLJTuning.unwind(iterators...)
12×3 Matrix{Any}:
 1  "a"  "x"
 2  "a"  "x"
 1  "b"  "x"
 2  "b"  "x"
 1  "a"  "y"
 2  "a"  "y"
 1  "b"  "y"
 2  "b"  "y"
 1  "a"  "z"
 2  "a"  "z"
 1  "b"  "z"
 2  "b"  "z"
```
