```
connectivity(model::AbstractModel)
```

[nₑ × nₙ] スパース行列を取得します。ここで、C[i, j] = -1 は要素 i がノード j で始まる場合、C[i,j] = 1 は要素 i がノード j で終わる場合、その他の場合は 0 です。
