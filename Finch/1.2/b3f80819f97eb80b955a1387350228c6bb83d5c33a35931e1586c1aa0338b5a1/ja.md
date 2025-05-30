```
ElementLevel{Vf, [Tv=typeof(Vf)], [Tp=Int], [Val]}()
```

要素レベルのサブファイバーは、`Tv`型のスカラーであり、`Vf`で初期化されます。`Vf`はオプションで最初の引数として指定できます。

データは、`eltype(Val) = Tv`の型`Val`のベクターに格納されます。型`Tp`は、Valにアクセスするために使用されるインデックス型です。

```jldoctest
julia> tensor_tree(Tensor(Dense(Element(0.0)), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: 1.0
   ├─ [2]: 2.0
   └─ [3]: 3.0
```
