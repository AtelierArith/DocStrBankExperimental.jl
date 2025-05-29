```
adapt(to, x)
```

値 `x` を `to` に応じて適応させます。`to` に対して特定の適応が登録されていない場合、この呼び出しは何もしません。

動作を変更するには、`adapt_structure` と `adapt_storage` のメソッドを実装して、それぞれ構造体を適応させる方法と、その構造体の葉を適応させる方法を定義します。

例えば、整数を持てない環境のためのアダプタを定義し、整数を浮動小数点数に適切に変換するための `adapt_storage` のメソッドを追加します：

```
julia> struct IntegerLessAdaptor end

julia> Adapt.adapt_storage(::IntegerLessAdaptor, x::Int64) = Float64(x)

julia> adapt(IntegerLessAdaptor(), 42)
42.0
```

これは既知の型にも自動的に機能します：

```
julia> adapt(IntegerLessAdaptor(), tuple(1,2,3))
(1.0, 2.0, 3.0)
```

カスタム構造体でこれを機能させたい場合は、`adapt_structure` を拡張する必要があります：

```
julia> struct MyStructure
         x
       end

julia> Adapt.adapt_structure(to, obj::MyStructure) = MyStructure(adapt(to, obj.x))

julia> adapt(IntegerLessAdaptor(), MyStructure(42))
MyStructure(42.0)
```
