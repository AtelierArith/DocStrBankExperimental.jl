```
@opt_out frule([config], _, f, args...)
@opt_out rrule([config], f, args...)
```

これにより、ADシステムを使用して微分することを示す、より具体的なメソッドを提供することで、`frule`または`rrule`からオプトアウトできます。

例えば、`foo(x::AbtractArray)`という関数を考えてみましょう。一般的に、`rrule`を実装するための効率的で汎用的な方法を知っています。そうすることで、（おそらく[`ProjectTo`](@ref)を利用して）実装します。しかし、実際には、特定の`FancyArray`型に対しては、ADにその処理を任せる方が良いことがわかります。

その場合、次のように書きます。

```julia
function rrule(::typeof(foo), x::AbstractArray)
    foo_pullback(ȳ) = ...
    return foo(x), foo_pullback
end

@opt_out rrule(::typeof(foo), ::FancyArray)
```

これにより、`nothing`を返す[`rrule`](@ref)が生成され、[`ChainRulesCore.no_rrule`](@ref)に類似のエントリも追加されます。

[`frule`](@ref)および[`ChainRulesCore.no_frule`](@ref)についても同様のことが適用されます。

詳細については、[ルールからのオプトアウトに関するドキュメント](@ref opt_out)を参照してください。
