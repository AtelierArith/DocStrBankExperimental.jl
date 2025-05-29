```
vectors_set(daf::DafReader, axis::AbstractString)::AbstractSet{<:AbstractString}
```

`daf`の`axis`に対するベクトルプロパティの名前、**特別な`name`プロパティを含まない**。

まず、`axis`が`daf`に存在することを確認します。

!!! note
    Juliaには返すための不変のセット型がありません。結果のセットを変更すると、悪いことが*起こる*でしょう。

