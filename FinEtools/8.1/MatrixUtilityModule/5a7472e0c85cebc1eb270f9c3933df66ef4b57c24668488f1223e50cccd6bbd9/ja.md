```
matrix_blocked_df(A, row_nfreedofs, col_nfreedofs = row_nfreedofs)
```

行列の「データフリー」部分を抽出します。

行列は4つのブロックで構成されていると仮定します。

```
A = [A_ff A_fd
     A_df A_dd]
```

ここで `f` は自由を、`d` はデータ（すなわち固定、指定された、...）を表します。`ff` ブロックのサイズは `row_nfreedofs, col_nfreedofs` です。どのブロックも正方形ではなく、`row_nfreedofs == col_nfreedofs` の場合のみ正方形になります。

`row_nfreedofs == col_nfreedofs` の場合、行数のみを指定する必要があります。
