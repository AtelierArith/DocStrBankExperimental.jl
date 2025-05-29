```julia_skip
@pack! dict_or_typeinstance = a, b, c, ...
```

変数を可変合成型、`Dict{Symbol}`、または`Dict{String}`にパックします。

辞書を使った例：

```julia
a = 5.0
c = "Hi!"
d = Dict{Symbol,Any}()
@pack! d = a, c
d # Dict{Symbol,Any}(:a=>5.0,:c=>"Hi!")
```

型を使った例：

```julia
a = 99
c = "HaHa"
mutable struct A; a; b; c; end
d = A(4,7.0,"Hi")
@pack! d = a, c
d.a == 99 #true
d.c == "HaHa" #true
```

その機能は、`UnPack.pack!`関数にメソッドを追加することで拡張できます。

不変のものを「パック」するには、Setfield.jlパッケージを使用してください。
