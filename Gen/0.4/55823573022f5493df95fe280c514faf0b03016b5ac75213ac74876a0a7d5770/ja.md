```
(new_trace, accepted) = metropolis_hastings(
    trace, selection::Selection;
    check=false, observations=EmptyChoiceMap())
```

選択されたアドレスの新しい値を内部提案から提案するメトロポリス-ヘイスティングス更新を実行します（通常は祖先サンプリングを使用）。新しいトレースを返し（移動が受け入れられなかった場合は前のトレースと等しい）、移動が受け入れられたかどうかを示すBoolを返します。
