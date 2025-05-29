```
getproperties(obj)::NamedTuple
getproperties(obj::Tuple)::Tuple
```

`obj`のプロパティを`NamedTuple`として返します。`Tuple`はシンボリックプロパティを持たないため、`getproperties`はタプルに対する恒等関数です。

# 例

```jldoctest
julia> using ConstructionBase

julia> struct S
           a
           b
           c
       end

julia> s = S(1, 2, 3)
S(1, 2, 3)

julia> getproperties(s)
(a = 1, b = 2, c = 3)

julia> getproperties((10,20))
(10, 20)
```

## 仕様

`getproperties`は[セマンティックレベル](@ref the-semantic-level)に属します。`getproperties`はいくつかの不変条件を保証します。オーバーロードする際は、ユーザーがそれらを確保する責任があります：

1. `getproperties`は`Base.propertynames`、`Base.getproperty`、`Base.setproperty!`と一貫性があるべきです。意味的には次のように等価であるべきです：  `julia  function getproperties(obj)      fnames = propertynames(obj)      NamedTuple{fnames}(getproperty.(Ref(obj), fnames))  end`
2. `getproperties`は`setproperties`に関連して定義されており、次のようになります：

    `julia  obj == setproperties(obj, getproperties(obj))`

    このセマンティクスからの唯一の例外は、未定義のプロパティが`getproperties`の返り値に含まれない場合です。

# 実装

`getproperties`はすべてのオブジェクトに対してデフォルトで定義されています。カスタム型`MyType`が`getproperties(obj::MyType)`を実装する必要があるのは非常に稀です。その理由は、未定義のフィールドやパフォーマンスの考慮です。
