```
ctemplate = ColorMixture((rgb₁, rgb₂))        # N0f8 チャンネル強度のゼロの ColorMixture を作成
ctemplate = ColorMixture{T}((rgb₁, rgb₂))     # 同様だが、要素型を指定
c = ctemplate((i₁, i₂))                       # `ctemplate` と同じ型の非ゼロ ColorMixture を構築
```

ColorMixture "テンプレート" `ctemplate` を作成し、他の非ゼロカラー `c` を作成できるようにします。

`ctemplate((i...,))` は、`ctemplate` の型が知られている場合にパフォーマンスに優れたコンストラクタ形式です。[関数バリア](https://docs.julialang.org/en/v1/manual/performance-tips/#kernel-functions) と組み合わせることで、推論の悪さによるパフォーマンスの問題を回避するためにこの形式を使用できます。
