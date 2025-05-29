コーパスをトークン化し、結果として得られたトークンのベクトルを文ごとにチャンクします。結果は、URNとシーケンス番号を持つ`NamedTuple`のベクトルです。URNはトークンの範囲です。

```julia
parsesentences(c, ortho; terminators)

```
