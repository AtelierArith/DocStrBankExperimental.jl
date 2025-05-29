```
checktokenised(txt::Txt) -> Vector{Int}
```

`txt`がトークン化されていない場合（`txt.is_tokenised == false`）、`TokeniseError`をスローします。それ以外の場合、トークンベクター`txt.tokenised`を返します。
