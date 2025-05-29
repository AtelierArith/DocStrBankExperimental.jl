```
train!(sol::AbstractCFRSolver, n; cb=()->(), show_progress=false)
```

`n` 回のイテレーションで CFR ソルバーをトレーニングし、オプションのコールバック `cb` とオプションのプログレスバー `show_progress` を指定します。
