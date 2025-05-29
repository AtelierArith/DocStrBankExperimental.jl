```
isfeasible(constraints::AbstractVector{<:HalfSpace}, [witness]::Bool=false;
           [solver]=nothing)
```

線形制約のリストの実現可能性をチェックします。

### 入力

  * `constraints` – 線形制約のリスト
  * `witness`     – （オプション; デフォルト: `false`）ウィットネス生成のフラグ
  * `solver`      – （オプション; デフォルト: `nothing`）LPソルバー

### 出力

`witness` が `false` の場合、結果は `Bool` です。

`witness` が `true` の場合、結果はペア `(res, w)` であり、`res` は `Bool` で、`w` はウィットネスポイント/ベクトルです。

### アルゴリズム

この実装は、制約を `tosimplehrep` を介して行列-ベクトル形式に変換し、結果に対して `isfeasible` を呼び出します。
