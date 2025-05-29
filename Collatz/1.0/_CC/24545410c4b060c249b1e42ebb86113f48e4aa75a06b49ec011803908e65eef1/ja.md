サイクル制御: ヘイルストーン列においてイベントが発生したときに示す記述フラグ、詳細表示に設定されている場合、または停止時間チェック。値を `_CC.ABC` のように参照するために列挙型をラップするために使用されるモジュール。

# 例

```jldoctest
julia> string(_CC.STOPPING_TIME)
"STOPPING_TIME"
julia> string(_CC.TOTAL_STOPPING_TIME)
"TOTAL_STOPPING_TIME"
julia> string(_CC.CYCLE_INIT)
"CYCLE_INIT"
julia> string(_CC.CYCLE_LENGTH)
"CYCLE_LENGTH"
julia> string(_CC.MAX_STOP_OOB)
"MAX_STOP_OOB"
julia> string(_CC.ZERO_STOP)
"ZERO_STOP"
```
