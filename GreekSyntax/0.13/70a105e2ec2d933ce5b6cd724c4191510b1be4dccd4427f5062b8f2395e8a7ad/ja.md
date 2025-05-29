トークン化されたトークンのベクトルを解析し、文ごとにチャンクします。結果は、URNとシーケンス番号を持つ`NamedTuple`のベクトルです。URNはトークンの範囲です。

```julia
parsesentences(v, ortho; terminators)

```
