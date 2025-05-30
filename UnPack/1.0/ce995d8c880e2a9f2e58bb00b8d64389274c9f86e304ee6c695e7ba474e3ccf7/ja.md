```julia_skip
@unpack a, b, c, ... = dict_or_typeinstance
```

複合型、`Dict{Symbol}`、`Dict{String}`、またはモジュールから変数にフィールド/プロパティ/キーをアンパックします。

辞書を使った例：

```julia
d = Dict{Symbol,Any}(:a=>5.0,:b=>2,:c=>"Hi!")
@unpack a, c = d
a == 5.0 #true
c == "Hi!" #true
```

型を使った例：

```julia
struct A; a; b; c; end
d = A(4,7.0,"Hi")
@unpack a, c = d
a == 4 #true
c == "Hi" #true
```

その機能は、`UnPack.unpack`関数にメソッドを追加することで拡張できます。
