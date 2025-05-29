```
convert_unit(from,to,val)
```

`from`に格納されている単位から`to`に格納されている単位に単位を変換します。

両方の単位が等しい場合、単に`val`を返します。

`val`自体が`unit`である場合、`val`の単位から`to`の単位に変換します。

# 例

```julia-repl
julia> convert_unit(u"Pa",u"kPa",1000.0)      
1.0
```

```julia-repl
julia> convert_unit(u"Pa",u"kPa",1u"atm")     
4053//40
```
