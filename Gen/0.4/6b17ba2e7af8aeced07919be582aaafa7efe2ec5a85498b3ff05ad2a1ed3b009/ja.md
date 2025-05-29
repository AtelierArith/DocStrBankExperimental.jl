```
(new_trace, accepted) = metropolis_hastings(
    trace, proposal::GenerativeFunction, proposal_args::Tuple;
    check=false, observations=EmptyChoiceMap())
```

与えられたトレース内のランダムな選択肢の一部に対して新しい値を提案するメトロポリス-ヘイスティングスの更新を行い、移動が受け入れられなかった場合は前のトレースと等しい新しいトレースと、移動が受け入れられたかどうかを示すBoolを返します。

提案生成関数は、最初の引数としてモデルの現在のトレースを受け取り、残りの引数として`proposal_args`を受け取る必要があります。提案がモデル内の制御フローを決定するアドレスを変更する場合、モデルによって新たにサンプリングされたアドレスに対しては、提案が値を提供する必要があります。
