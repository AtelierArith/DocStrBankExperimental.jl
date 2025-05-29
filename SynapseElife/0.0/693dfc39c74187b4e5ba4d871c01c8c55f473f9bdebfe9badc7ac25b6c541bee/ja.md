```julia
firingPattern(
;
    start_time,
    n_pre,
    delay_pre,
    n_pos,
    delay_pos,
    delay,
    pulse,
    freq,
    causal,
    repeat_times,
    repeat_after
)

```

外部刺激の時間とインデックスを生成します。通常は `dataProtocol` と一緒に使用されます（`examples/` フォルダ内の例を参照）。

# 出力

  * `event_times` 外部イベント時間のソートされたリスト
  * `is_pre_or_post_index` 外部イベントが前（`true`）か後（`false`）かを示します
