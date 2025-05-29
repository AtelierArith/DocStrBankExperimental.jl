```
num_supports(prefs::AbstractArray{<:DependentParameterRef};
             [label::Type{<:AbstractSupportLabel} = PublicLabel])::Int
```

依存する無限パラメータ `prefs` に関連付けられたサポートポイントの数を返します。すべてが同じ基礎オブジェクトからでない場合はエラーになります。`label` を指定することで、`label` を持つサポートのみをカウントするサポートのサブセットを指定できます。デフォルトでは、公開サポートの数のみが与えられますが、`label == All` を使用することで全体の数を取得できます。

**例**

```julia-repl
julia> num_supports(x)
2
```
