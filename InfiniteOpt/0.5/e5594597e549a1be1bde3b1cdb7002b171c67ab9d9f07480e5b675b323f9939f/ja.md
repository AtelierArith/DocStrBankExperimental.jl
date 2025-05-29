```
supports_in_domain(supports::Union{Real, Vector{<:Real}, Array{<:Real, 2}},
                domain::AbstractInfiniteDomain)::Bool
```

`supports` が `domain` の範囲内にあるかどうかを確認するために使用されます。`supports` が `domain` の範囲内にある場合は `true` を返し、それ以外の場合は `false` を返します。これは主にチェックを行うための内部メソッドですが、ユーザー定義のドメインタイプに対して拡張することができます。これを拡張することは任意ですが、可能な限り推奨されます。フォールバックとして、これは認識されないドメインタイプに対して `true` を返すため、エラーは発生しません。
