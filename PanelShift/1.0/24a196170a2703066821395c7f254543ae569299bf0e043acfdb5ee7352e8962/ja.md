```
panelshift!(df, id, t, x, newx, n=oneunit(df[1, t] - df[1, t]); checksorted=true)
```

データフレーム `df` 内で、`id` によってインデックス付けされた各グループについて、時間列 `t` に対して `n` 期間だけ列 `x` をシフトし、シフトされた列を `newx` という名前で保存します。引数 `id`、`t`、`x`、および `newx` はすべて `df` の列インデックスです。

`n` が正の場合は `tlag` を呼び出し、`n` が負の場合は `tlead` を呼び出します。

`panellead!`、`panellag!` も参照してください。
