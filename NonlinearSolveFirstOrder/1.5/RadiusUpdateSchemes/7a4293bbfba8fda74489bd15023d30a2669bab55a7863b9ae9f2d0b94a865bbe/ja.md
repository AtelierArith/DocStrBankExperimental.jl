```
RadiusUpdateSchemes
```

`RadiusUpdateSchemes` は、信頼領域法で実装されたさまざまなタイプの半径更新スキームを提供します。これらのスキームは、アルゴリズムの各反復後にいわゆる信頼領域の半径がどのように更新されるかを指定します。各スキームに関連する具体的な役割と注意点は以下に示されています。

## `RadiusUpdateSchemes` の使用

単純に、次のように希望するスキームを指定します: `sol = solve(prob, alg = TrustRegion(radius_update_scheme = RadiusUpdateSchemes.Hei))`。
