```
isfeasible(A::AbstractMatrix, b::AbstractVector, [witness]::Bool=false;
           [solver]=nothing)
```

行列ベクトル形式で与えられた線形制約の実現可能性をチェックします。

### 入力

  * `A`       – 制約行列
  * `b`       – 制約ベクトル
  * `witness` – （オプション; デフォルト: `false`）ウィットネス生成のフラグ
  * `solver`  – （オプション; デフォルト: `nothing`）LPソルバー

### 出力

`witness` が `false` の場合、結果は `Bool` です。

`witness` が `true` の場合、結果はペア `(res, w)` であり、`res` は `Bool` で、`w` はウィットネスポイント/ベクトルです。

### アルゴリズム

この実装は、対応する実現可能性線形プログラムを解決します。
