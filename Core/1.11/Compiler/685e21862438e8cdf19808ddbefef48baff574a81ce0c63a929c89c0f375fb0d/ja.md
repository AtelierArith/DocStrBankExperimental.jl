```
widenreturn(𝕃ᵢ::AbstractLattice, @nospecialize(rt), info::BestguessInfo) -> new_bestguess
widenreturn_noslotwrapper(𝕃ᵢ::AbstractLattice, @nospecialize(rt), info::BestguessInfo) -> new_bestguess
```

適切に推論された戻り値 `rt` の型を、キャッシュに保存でき、かつ手続き間で有効かつ良好な型に変換します。例えば、`rt isa Conditional` の場合、`rt` は `InterConditional` または他のキャッシュ可能なラティス要素に変換されるべきです。

外部ラティス `𝕃ᵢ::ExternalLattice` は以下をオーバーロードすることができます：

  * `widenreturn(𝕃ᵢ::ExternalLattice, @nospecialize(rt), info::BestguessInfo)`
  * `widenreturn_noslotwrapper(𝕃ᵢ::ExternalLattice, @nospecialize(rt), info::BestguessInfo)`

```
