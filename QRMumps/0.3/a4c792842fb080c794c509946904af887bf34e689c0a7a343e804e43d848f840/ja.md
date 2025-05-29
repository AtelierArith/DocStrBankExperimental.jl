```
qrm_update_shift_spmat!(shifted_spmat, α)
```

与えられた `shifted` ブロック行列の形 `(A  √α)` において、行列内のパラメータ `α` を更新します。

### 入力引数

  * `shifted_spmat`: qrm*shifted*spmat 型の入力行列。詳細については `qrm_shifted_spmat` を参照してください。
  * `α ≥ 0`: 正則化パラメータ（ブロック行列表現における平方根に注意してください）。
