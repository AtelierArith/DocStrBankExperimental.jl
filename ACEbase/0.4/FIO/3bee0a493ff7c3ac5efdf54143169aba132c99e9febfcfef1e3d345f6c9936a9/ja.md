`read_dict(D::Dict) -> ?`

`D`の中に`__id__`というキーを探し、その値を使ってデコードを動的にディスパッチします。

```julia
read_dict(Val(Symbol(D["__id__"])), D)
```

つまり、ユーザー定義型はこの`convert(::Val, ::Dict)`ユーティリティ関数を実装する必要があります。典型的なコードは次のようになります。

```julia
module MyModule
    struct MyStructA
        a::Float64
    end
    Dict(A::MyStructA) = Dict( "__id__" -> "MyModule_MyStructA",
                               "a" -> a )
    MyStructA(D::Dict) = A(D["a"])
    Base.convert(::Val{:MyModule_MyStructA})
end
```

ユーザーは十分にユニークなIDを選択する責任があります。

この関数の目的は、より複雑なJSONファイルの読み込みを可能にし、解析されたDictを適切な複合型に自動的に変換することです。ここでユーザーコードにかなりの負担がかかるのは意図的です。これにより、バージョン番号を導入したり、将来的に古いバージョンを読み込んだりすることで、柔軟性が最大化されます。
