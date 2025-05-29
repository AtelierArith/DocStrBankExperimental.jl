```
acvf(model, θ, lagMax, ofλ)
```

INGARCH(p, q)プロセスの自己共分散関数。回帰子や対数リンクを持つモデルは対象外です。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）
  * `lagMax`: 計算する最大ラグ
  * `ofλ`: trueの場合、条件付き平均系列のACVF/ACFを返す

# 例

```julia-repl
model = Model(pastObs = 1)
acvf(model, [10, 0.5])
```
