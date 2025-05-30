```julia
struct RegularJump{iip, R, C, MD}
```

τ-リープ型メソッドで使用するためのレートと複数の同時ジャンプをエンコードするための表現。

### コンストラクタ

  * `RegularJump(rate, c, numjumps; mark_dist = nothing)`

## フィールド

  * `rate`: 現在のレート、すなわちすべての可能なジャンプに対する強度または傾向を返す関数 `rate!(rate_vals, u, p, t)`。
  * `c`: `i` 番目のジャンプを `counts[i]` 回実行し、出力を `du[i]` に保存する関数 `c(du, u, p, t, counts, mark)`。
  * `numjumps`: システム内のジャンプの数。
  * `mark_dist`: マークの分布。現在は使用されていないか、サポートされていません。

## 例

```julia
function rate!(out, u, p, t)
    out[1] = (0.1 / 1000.0) * u[1] * u[2]
    out[2] = 0.01u[2]
    nothing
end

const dc = zeros(3,2)
function c(du, u, p, t, counts, mark) 
    mul!(du, dc, counts)
    nothing
end

rj = RegularJump(rate!, c, 2)

## ノート
- `mark_dist` は現在 τ-リープメソッドでは使用されていないか、サポートされていません。
```
