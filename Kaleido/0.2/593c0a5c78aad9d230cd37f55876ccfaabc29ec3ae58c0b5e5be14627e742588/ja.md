```
constraining(f; onget=true, onset=true)
```

呼び出し可能な `f` によって制約を課すレンズを作成します。

  * 呼び出し可能な `f` は冪等でなければなりません。すなわち、`f ∘ f = f` です。
  * 元のオブジェクトがすでに制約を満たしている場合（すなわち `f(obj) == obj`）、`onget=false` を渡すことで `get` 中に `f` を呼び出すのをスキップできます。

# 例

```jldoctest
julia> using Kaleido, Setfield

julia> obj = (a = 1, b = 1);

julia> constraint = constraining() do obj
           @set obj.b = obj.a
       end
constraining(#1)

julia> lens = constraint ∘ @lens _.a
constraining(#1) ∘ (@lens _.a)

julia> get(obj, lens)
1

julia> set(obj, lens, 2)
(a = 2, b = 2)
```

`constraining` は [`@batchlens`](@ref) や [`MultiLens`](@ref) と組み合わせると便利です：

```jldoctest
julia> using Kaleido, Setfield

julia> obj = (a = 1, b = 2, c = 3);

julia> constraint = constraining() do obj
           @set obj.c = obj.a + obj.b
       end;

julia> lens = constraint ∘ MultiLens((
           (@lens _.a),
           (@lens _.b),
       ));

julia> get(obj, lens)
(1, 2)

julia> set(obj, lens, (100, 20))
(a = 100, b = 20, c = 120)
```
