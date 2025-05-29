```
FlashResult(compositions,fractions,volumes,data::FlashData)
FlashResult(model,p,T,z,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(model,p,T,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(model,p,T,z;phase = :unknown)
FlashResult(p,T,z,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(p,T,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(flash::FlashResult,g = nothing;sort = true)
```

フラッシュの結果を含むために使用される構造体。モル組成のリスト、相ごとのモル量のリスト、モル体積のリスト、および圧力、温度、縮退ギブズエネルギーを含む補助構造体 `FlashData` を含みます。`EoSModel` が `FlashResult` の入力として使用される場合、提供されていない場合は縮退モルギブズエネルギー (g = g/NRT) が計算されます。デフォルトでは、相は体積でソートされますが、キーワード引数 `sort = false` を渡すことで変更できます。`FlashResult(model,p,T,z;phase)` は単一相の `FlashResult` を構築します。バルク組成 `z` が提供されると、それは分数をスケーリングするために使用され、`sum(fractions) == sum(z)` を強制します。
