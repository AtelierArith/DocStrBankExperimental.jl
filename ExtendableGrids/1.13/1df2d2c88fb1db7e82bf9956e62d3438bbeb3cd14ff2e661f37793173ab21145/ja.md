```julia
trytoken(
    tks::ExtendableGrids.TokenStream,
    expected::String
) -> Bool

```

キーワードトークンを試します。

トークンが欠落している場合、読み取られたトークンはストリームに戻され、falseの値が返され、次のtry/gettokenコマンドは同じ位置から続行されます。

そうでなければ、trueが返され、トークンが見つかった後に読み取りが続行されます。
