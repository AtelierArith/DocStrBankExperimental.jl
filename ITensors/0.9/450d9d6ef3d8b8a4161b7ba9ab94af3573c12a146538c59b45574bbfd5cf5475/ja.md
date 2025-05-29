```
diag_itensor([ElT::Type, ]v::AbstractVector, inds...)
diagitensor([ElT::Type, ]v::AbstractVector, inds...)
```

対角線上にのみ非ゼロ要素を持つスパースITensorを作成します。一般に、対角要素は`v`に格納されているものであり、ITensorの要素型は`eltype(v)`になりますが、`ElT`で明示的に指定された場合を除きます。ストレージは`NDTensors.Diag`型になります。

`eltype(v) isa Union{Int, Complex{Int}}`の場合、デフォルトでは`float(v)`に変換されます。この動作は将来的に変更される可能性があることに注意してください。

`diag_itensor`バージョンは、入力ベクトルデータのエイリアスであるストレージデータを持つITensorを決して出力しません。

`diagitensor`バージョンは、操作を最小限に抑えるために、入力ベクトルデータのエイリアスであるストレージデータを持つITensorを出力する可能性があります。
