```
LShapedAlgorithm
```

L-shapedアルゴリズムのファンクタオブジェクト。

...

# アルゴリズムパラメータ

  * `τ::AbstractFloat = 1e-6`: 収束チェックのための相対許容誤差。
  * `debug::Bool = false`: デバッグ目的で追加情報を保存するかどうかを指定します。メモリ効率のためにデフォルトはfalseです。
  * `cut_scaling::AbstractFloat = 1.0`: 数値的安定性を向上させるためのカッティングプレーンの再スケーリング係数。
  * `log::Bool = true`: L-shaped手続きが標準出力にログされるべきかどうかを指定します。

...
