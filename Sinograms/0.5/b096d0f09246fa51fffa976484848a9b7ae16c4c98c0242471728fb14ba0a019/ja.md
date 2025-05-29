```
plan = plan_fbp(rg, ig; window=Window(), ...)
```

平面FDK 3D CBCT画像再構成、フラットまたはアーク検出器のいずれかを使用します。

このメソッドを使用するには、まずCTジオメトリと画像ジオメトリを指定して呼び出します。このルーチンは初期化された`plan`を返します。その後、FDK再構成を実行するには、`plan`を使って`fbp`を呼び出します（同じジオメトリに対して何度も呼び出すことができます）。

# 入力

  * `rg::CtGeom`
  * `ig::ImageGeom` は `ig.mask` 内のピクセルのみを再構成します。

# オプション

  * `window::Window` 例: `Window(Hamming(), 0.8)`; デフォルトは `Window()`
  * `npad::Int` パディング後の放射ビンの数; デフォルトは `nextpow(2, rg.ns + 1)`
  * `decon1::Bool` 補間器の効果を逆変換しますか？（デフォルトは `true`）

# 出力

  * `plan::FDKplan` 初期化されたプラン

```
