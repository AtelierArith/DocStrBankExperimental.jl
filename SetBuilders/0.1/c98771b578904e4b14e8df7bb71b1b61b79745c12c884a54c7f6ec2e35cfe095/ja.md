```
@setbuild([args...[; kwargs...]])
```

`@setbuild` マクロは、さまざまな SetBuilders セットを作成します。

引数の数は、作成するセットのタイプによって異なります。

## 引数なし

  * EmptySet

```julia-repl
julia> @setbuild()
EmptySet()
```

## 引数1つ

  * TypeSet

最初の引数は任意の Julia 型です。

```julia-repl
julia> @setbuild(Integer)
TypeSet(Integer)
```

  * EnumerableSet

最初の引数は、オプションで Julia 型を持つベクターです。

```julia-repl
julia> @setbuild([1, 2, 3])
EnumerableSet([{Int64}*3])

julia> @setbuild(Int32[])
EnumerableSet([{Int32}*0])
```

  * UniversalSet

最初の引数は `Any` 型です。

```julia-repl
julia> @setbuild(Any)
UniversalSet()
```

## 引数2つ

  * PredicateSet

最初の引数はセットのドメインです。2番目の引数はセットの述語です。

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> @setbuild(x in I, 0 <= x < 5)
PredicateSet((x ∈ TypeSet(Integer)) where 0 <= x < 5)
```

## 引数4つ

  * MappedSet

最初の引数はセットのドメインです。2番目の引数はセットのコドメインです。3番目の引数はセットの前方マッピングです。4番目の引数はセットの後方マッピングです。

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> @setbuild(x in I, y in I, y = x + 1, x = y - 1)
MappedSet((x ∈ TypeSet(Integer)) -> (y ∈ TypeSet(Integer)))
```

## キーワード引数

キーワード引数の主な使用法は、`@setbuild` 内の式に `@setbuild` の外で定義されたオブジェクトを提供することです。

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> k = 1
1

julia> @setbuild(x in I, y in I, y = x + c, x = y - c, c=k)
MappedSet((x ∈ TypeSet(Integer)) -> (y ∈ TypeSet(Integer)))
```

# キーワード

キーワード引数は、`@setbuild` マクロに名前付き参照を提供するために使用されます。たとえば、前のコード例では、`c=k` キーワード引数が `@setbuild` マクロに `k` の値を提供し、`y = x + c` または `x = y - c` が正しく評価されるようにします。

!!! note
    "sb_" で始まるキーワード名は SetBuilders の内部使用のために予約されています。


```
