`toexpr(c::Context, t) -> Any`

GATlabの構文を、`fromexpr`を介して読み込むことができるExprに変換します。重要なことに、これの出力は`c`のスコープの順序に依存し、異なる`c`で読み戻すと異なる結果になる可能性があります。
