```
add_generative_supports(pref::IndependentParameterRef)::Nothing
```

`pref` に必要に応じて生成サポートを作成し、その生成サポート情報に従って [`make_generative_supports`](@ref) を使用してそれらを `pref` に追加します。これは内部関数として意図されていますが、私たちのサポートシステムを利用するユーザー定義の最適化モデル拡張に役立つ場合があります。
