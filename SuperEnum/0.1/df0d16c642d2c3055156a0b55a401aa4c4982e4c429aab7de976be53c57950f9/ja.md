```
@se EnumName[::BaseType] value1[=x] value2[=y]
@se EnumName[::BaseType] value1[=>string1] value2[=>string2]
```

`Enum{BaseType}`のサブタイプを作成し、名前を`EnumName`とし、列挙メンバーの値を`value1`と`value2`にし、それぞれオプションで`x`と`y`の値を割り当てるか、`type=>description`のペアを使用します。`EnumName`は`EnumName.EnumNameEnum`として定義され、ここで`EnumName`はモジュールで、`EnumNameEnum`は型です。この型は他の型と同様に使用でき、列挙メンバーの値は通常の値として使用できます。

# 例

```jldoctest fruitenum
julia> @se Fruit apple=1 orange=2 kiwi=3
julia> f(x::Fruit) = "I'm a Fruit with value: $(Int(x))"
f (generic function with 1 method)
julia> f(apple)
"I'm a Fruit with value: 1"
julia> Fruit(1)
apple::Fruit = 1
julia> SuperEnum.@se Lang zh=>"中文" en=>"English" ja=>"日本语"
WARNING: replacing module Lang.
Main.Lang
julia> string(Lang.zh)
"中文"
julia> string(Lang.en)
"English"
julia> string(Lang.ja)
"日本语"
julia> Lang.LangEnum
Enum Main.Lang.LangEnum:
zh = 0
en = 1
ja = 2
```

値は`begin`ブロック内でも指定できます。例えば、

```julia
@se EnumName begin
    value1
    value2
end
```

`BaseType`はデフォルトで[`Int32`](@ref)であり、`Integer`のプリミティブサブタイプでなければなりません。メンバー値は列挙型と`BaseType`の間で変換できます。`read`と`write`はこれらの変換を自動的に行います。列挙のすべてのインスタンスをリストするには`instances`を使用します。例えば、

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```
