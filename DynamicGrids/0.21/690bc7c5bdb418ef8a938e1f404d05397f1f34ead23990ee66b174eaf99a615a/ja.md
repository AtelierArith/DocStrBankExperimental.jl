```
Extent <: AbstractExtent

Extent(init, mask, aux, padval, tspan)
Extent(; init, tspan, mask=nothing, aux=nothing, padval=zero(eltype(init)), kw...)
```

広範な変数のコンテナ：空間データと時系列データ。これらはルールから分離されており、ルールを異なる空間および時間のコンテキストに適用できるようにしています。

Extentは通常、ユーザーによって直接構築されることはありませんが、`Output`コンストラクタに`init`、`mask`、`aux`、および`tspan`の代わりに渡すことができます。

# 引数/キーワード

  * `init`: グリッド用の初期化`Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための`BitArray`。
  * `aux`: 任意の入力データのNamedTuple。`Rule`から型安定な方法でアクセスするには、`aux(data, Aux(:key))`を使用します。
  * `padval`: 隣接ルールを持つグリッドのためのパディング値。デフォルトは`zero(eltype(init))`です。
  * `tspan`: 時間範囲。決して型安定ではなく、`modifyrule`メソッド内でのみアクセスしてください。
