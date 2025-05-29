```
SeparateLevel{Lvl, [Val]}()
```

Separate levelのサブファイバーは、独自のメモリ空間にあるタイプ`Lvl`の別のテンソルです。

各サブレベルは、`eltype(Val) = Lvl`のタイプ`Val`のベクターに格納されます。

```jldoctest
julia> tensor_tree(Tensor(Dense(Separate(Element(0.0))), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: Pointer ->
   │  └─ 1.0
   ├─ [2]: Pointer ->
   │  └─ 2.0
   └─ [3]: Pointer ->
      └─ 3.0
```
