```
score = lecture!(
    p::GenerativeFunction, p_args::Tuple,
    q::GenerativeFunction, get_q_args::Function)
```

pを表すトレースをシミュレートし、それを使用してqの学習可能なパラメータの勾配を更新します。

これは、最大期待条件付き尤度を介してqをトレーニングするために使用されます。ランダムな選択は、そのアドレスに基づいてpからqにマッピングされます。get*q*argsはpのトレースをqの引数タプルにマッピングします。scoreは条件付き対数尤度（または、qのすべてのランダム選択が制約されていない場合、またはqが非アドレス可能なランダム性を使用する場合のそれに対するバイアスのない下限の推定値）です。
