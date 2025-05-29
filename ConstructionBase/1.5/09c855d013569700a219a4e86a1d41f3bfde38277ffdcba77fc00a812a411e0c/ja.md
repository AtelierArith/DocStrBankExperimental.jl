```
setproperties(obj, patch::NamedTuple)
```

`patch`に従ってプロパティを更新した`obj`のコピーを返します。

# 例

```jldoctest
julia> using ConstructionBase

julia> struct S
           a
           b
           c
       end

julia> s = S(1,2,3)
S(1, 2, 3)

julia> setproperties(s, (a=10,c=4))
S(10, 2, 4)

julia> setproperties((a=1,c=2,b=3), (a=10,c=4))
(a = 10, c = 4, b = 3)
```

キーワードから`patch`引数を構築する便利なメソッドもあります：

```
setproperties(obj; kw...)
```

# 例

```jldoctest
julia> using ConstructionBase

julia> struct S
           a
           b
           c
       end

julia> o = S(10, 2, 4)
S(10, 2, 4)

julia> setproperties(o, a="A", c="cc")
S("A", 2, "cc")
```

## 仕様

`setproperties`は[セマンティックレベル](@ref the-semantic-level)に属します。以下の不変条件を満たす必要があります：

1. 純粋性：`setproperties`は副作用を持たないとされています。特に`setproperties(obj, patch::NamedTuple)`は`obj`を変更してはなりません。
2. `propertynames`および`fieldnames`との関係：`setproperties`は`propertynames`および`getproperty`に関連し、`fieldnames`および`getfield`には関連しません。これは、`propertynames(obj)`の任意の部分集合`p₁, p₂, ..., pₙ`が有効なプロパティのセットであり、以下のレンズの法則が成り立つことを意味します。
3. `setproperties`は`getproperties`に関連して定義されており、次のようになります：

    `julia  obj == setproperties(obj, getproperties(obj))`
4. `setproperties`はレンズの法則を満たす必要があります：

任意の有効なプロパティのセット`p₁, p₂, ..., pₙ`について、次の等式が成り立たなければなりません：

  * 設定したものが得られます。

```julia
let obj′ = setproperties(obj, ($p₁=v₁, $p₂=v₂, ..., $pₙ=vₙ))
    @assert obj′.$p₁ == v₁
    @assert obj′.$p₂ == v₂
    ...
    @assert obj′.$pₙ == vₙ
end
```

  * 既にあったものを設定しても何も変わりません：

```julia
@assert setproperties(obj, ($p₁=obj.$p₁, $p₂=obj.$p₂, ..., $pₙ=obj.$pₙ)) == obj
```

  * 最後のセットが勝ちます：

```julia
let obj′ = setproperties(obj, ($p₁=v₁, $p₂=v₂, ..., $pₙ=vₙ)),
    obj′′ = setproperties(obj′, ($p₁=w₁, $p₂=w₂, ..., $pₙ=wₙ))
    @assert obj′′.$p₁ == w₁
    @assert obj′′.$p₂ == w₂
    ...
    @assert obj′′.$pₙ == wₙ
end
```

# 実装

カスタム型`MyType`の場合、`setproperties(obj::MyType, patch::NamedTuple)`メソッドを定義できます。その際、仕様に準拠していることを確認することが重要です。

  * 意味がある場合は[`constructorof`](@ref)をオーバーロードすることを優先してください（例：`getproperty`メソッドが定義されていない場合）。デフォルトの`setproperties`は`constructorof`と`getproperties`に基づいて定義されています。
  * `getproperty`がカスタマイズされている場合、`setproperties`を定義するのは良いアイデアかもしれません。

!!! 警告     シグネチャ`setproperties(obj::MyType; kw...)`は決してオーバーロードしてはいけません。代わりに`setproperties(obj::MyType, patch::NamedTuple)`をオーバーロードするべきです。 ```
