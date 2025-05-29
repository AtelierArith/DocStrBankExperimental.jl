```
apply(f::Function, patches::Pair...)
```

指定された `patches` が適用された状態で関数 `f` を実行します。パッチはグローバルスイッチが有効な場合にのみ効果があります。詳細は [`Pretend.activate`](@ref) を参照してください。

`patches` 引数の各パッチは、元の関数とパッチ関数のペアです。パッチ関数が単一のオブジェクト `Fallback()` を返す場合、元の関数が実行されます。これは条件付きパッチを実装するための簡単なメカニズムを提供します。

# 例

```jldoctest
julia> @mockable add(x, y) = x + y;

julia> apply(add => (x,y) -> x - y) do
           @show add(1, 2)
       end;
add(1, 2) = -1

julia> apply(add => (x,y) -> x == y ? 0 : Fallback()) do
           @show add(1, 2)
           @show add(5, 5)
       end;
add(1, 2) = 3
add(5, 5) = 0
```
