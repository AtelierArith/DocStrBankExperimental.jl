```
レンダラー
```

`Renderer`は、特定の[`Domain`](@ref)に対するPDDL[`State`](@ref)がどのようにレンダリングされるべきかを定義します。PDDLドメイン（またはPDDLドメインのファミリー、例えば2Dグリッドワールド）用に具体的なサブタイプの`Renderer`を実装する必要があります。これは、そのドメインを視覚化したいユーザーのためです。

```
(r::Renderer)(domain::Domain, args...; options...)
(r::Renderer)(canvas::Canvas, domain::Domain, args...; options...)
```

`Renderer`が構築されると、適切な引数を使って呼び出すことで、PDDL状態や他のエンティティをレンダリングするために使用できます。
