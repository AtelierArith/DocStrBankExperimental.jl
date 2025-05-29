```julia
expecttoken(
    tks::ExtendableGrids.TokenStream,
    expected::String
) -> Bool

```

キーワードトークンを期待します。

トークンが欠落している場合、UnexpectedTokenErrorがスローされます。トークンが見つかった場合、読み取りは見つかったトークンの後の位置から続行されます。
