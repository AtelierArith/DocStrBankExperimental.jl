```
natural(q; base=u"eV")
```

`q`を`base`で指定された単位に基づいて自然単位に変換します。`base`が指定されていない場合、`natural`はデフォルトで`eV`を使用します。現在、`natural`はエネルギーの次元を持つ`base`のみをサポートしています。他のすべての`base`については、変換するために`unnatrual`を使用する必要があります。

例:

```
julia> natural(1u"kg")
5.609588650020686e35 eV

julia> natural(1u"kg", base=u"GeV")
5.609588650020685e26 GeV

julia> natural(1u"m")
5.067730759202785e6 eV^-1

julia> natural(1u"m", base=u"GeV")
5.067730759202785e15 GeV^-1
```
