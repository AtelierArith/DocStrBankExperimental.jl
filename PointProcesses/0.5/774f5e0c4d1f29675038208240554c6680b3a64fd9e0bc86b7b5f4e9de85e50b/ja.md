```
AbstractPoissonProcess{M} <: AbstractPointProcess{M}
```

すべての時間的ポアソン過程の共通インターフェース、つまり、強度が過去の履歴の関数でない時間的点過程です。

より少ない引数を受け入れる`AbstractPointProcess`インターフェースのいくつかのフォールバックを実装します。
