```
eeg_array_to_dataframe(data::AbstractMatrix, label_aliases::AbstractVector)
eeg_array_to_dataframe(data::AbstractVector, label_aliases::AbstractVector)
eeg_array_to_dataframe(data::Union{AbstractMatrix, AbstractVector{<:Number}})
```

配列（行列またはベクトル）を、列 `:estimate`、`:time`、および `:label`（エイリアス `:color`、`:group`、`:channel`）を持つ整然とした `DataFrame` に変換するヘルパー関数。

配列の形式:

  * プロット用の plot_erp のための times x condition。
  * プロット用の plot*butterfly、plot*topoplotseries のための channels x time。
  * プロット用の plot_topoplot のための channels。

**戻り値:** `DataFrame`。
