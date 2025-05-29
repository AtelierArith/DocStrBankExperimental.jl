タイプ: `GenericState`

メソッド: `update!`, `reinit!`

問題の状態を点 x で表すための一般的な State。

追跡されるデータには以下が含まれます：

  * x             : 現在の反復
  * d [opt]       : 探索方向
  * res [opt]     : 残差
  * current_time  : 時間
  * current_score : スコア

コンストラクタ:     `GenericState(:: T, :: S; d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64 = NaN) where {S, T <:AbstractVector}`

```
`GenericState(:: T; d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64 = NaN, current_score :: Union{T,eltype(T)} = _init_field(eltype(T))) where T <:AbstractVector`
```

注意:

  * デフォルトでは、未知のエントリは `_init_field` を使用して設定されます。
  * デフォルトで `current_score` の型は `eltype(x)` であり、State が作成された後は変更できません。長さ n のベクトル化された `current_score` を持つには、`GenericState(x, Array{eltype(x),1}(undef, n))` のように試してください。

例:   `GenericState(x)`   `GenericState(x, Array{eltype(x),1}(undef, length(x)))`   `GenericState(x, current_time = 1.0)`      `GenericState(x, current_score = 1.0)`

関連情報: `Stopping`, `NLPAtX`
