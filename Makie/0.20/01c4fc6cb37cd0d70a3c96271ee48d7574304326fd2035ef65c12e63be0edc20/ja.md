```
used_attributes(args...) = ()
```

関数は、`convert_arguments`に渡したいキーワード引数を示すために使用されます。これらの属性はバックエンドに転送されることはなく、変換パイプライン中にのみ使用されます。使用法：

```julia
    struct MyType end
    used_attributes(::MyType) = (:attribute,)
    function convert_arguments(x::MyType; attribute = 1)
        ...
    end
    # attributeはconvert_argumentsに渡されます
    # keyword_verloadがなければ、これは起こりません
    plot(MyType, attribute = 2)
    # 便利なマクロを使用して、1ステップでconvert_argumentsをオーバーロードすることもできます：
    @keywords convert_arguments(x::MyType; attribute = 1)
        ...
    end
```
