```
plan = plan_fbp(rg, ig; how=:normal, window=Window())
```

平行ビームおよびファンビームケースのための2Dトモグラフィー画像再構成のためのFBPプランで、ファンビームケースではフラットまたはアーク検出器のいずれかを使用します。

このメソッドを使用するには、まずシノグラムジオメトリと画像ジオメトリを指定して呼び出します。このルーチンは初期化された`plan`を返します。その後、FBP再構成を実行するには、`plan`を使って`fbp`を呼び出します（同じジオメトリに対して何度も呼び出すことができます）。

# in

  * `rg::SinoGeom`
  * `ig::ImageGeom` は `ig.mask` 内のピクセルのみを再構成します。

# option

  * `how::Symbol` 再構成方法

      * `:normal` デフォルト
      * `:mojette` モジェット再ビニングとGtomo2_tableを使用
  * `window::Window` 例: `Window(Hamming(), 0.8)`; デフォルト `Window()`
  * `npad::Int` パディング後の放射ビンの数; デフォルト `nextpow(2, rg.nb + 1)`
  * `decon1::Bool` 補間器効果をデコンボルブしますか？（デフォルト `true`）
  * `T::Type{<:Number}` `sino` 要素の型（デフォルト `Float32`）

# out

  * `plan::FBPplan` 初期化されたプラン
