`struct unvarSerF{𝕡,𝕩} <: AuxFunc where {𝕡<:PREC,𝕩<:EXAC}`

精度および正確性パラメータ化された、スカラー値、無次元、`<:AbstractFloat`、単変量、級数関数型で、明示的なコンパクト（有界/区間）ドメインサポートを持ちます。

正確性パラメータに応じて、*両方の*関数のドメインおよびコドメイン要素は、`𝕡 where {𝕡<:PREC}`型で均一であり、`𝕩 ≡ EX` — 正確なベースの場合；または`Measurement{𝕡} where {𝕡<:PREC}`型で、`𝕩 ≡ MM` — 測定ベースの場合です。

データメンバーには以下が含まれます：

```
- `xmin::Union{𝕡, Measurement{𝕡}} where 𝕡<:PREC`: ドメインサポート区間の下端点；
- `xmax::Union{𝕡, Measurement{𝕡}} where 𝕡<:PREC`: ドメインサポート区間の上端点；
- `fvec::Vector{Function}`: 関数の加法項の変数コレクション；
- `mulf::Union{𝕡, Measurement{𝕡}} where 𝕡<:PREC`: %誤差のための乗法因子；
```

内部コンストラクタは以下の基準/制限を強制します：

```
- 入力値 `{xmin,xmax}` は NaN であってはならない；
- `xmin <= xmax`；
- `fvec` は空であってはならない。
```

`unvarSerF` のインスタンスは `functors` であり、関数として使用できることを意味します（期待通り）。ファンクタの実装は以下の基準を強制します：もし `𝑓::unvarSerF{𝕡,𝕩} ...` であれば：

```
- `𝑓{𝕡,EX}(𝑥)::𝕡 where 𝕡<:PREC`、つまり戻り値の型の精度は `EX`；
- `𝑓{𝕡,MM}(𝑥)::Measurement{𝕡} where 𝕡<:PREC`、つまり戻り値の型の精度は `MM`；
```

## 階層

`unvarSerF <: AuxFunc <: AUX <: AbstractTherm <: Any`
