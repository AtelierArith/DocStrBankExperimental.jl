```
指定されたノード位置の辞書（`nodes`）と与えられた`bounds`内の選択された地図の特徴をプロットします。`km`パラメータを使用すると、メートルの代わりに地図のキロメートルスケールを持つことができます。

デフォルトのプロットバックエンドは`Plots.jl`で定義されているものですが、`use_plain_pyplot`が`true`に設定されている場合、Plots.pythonplot()が呼び出されてPythonPlotバックエンドに切り替わります（このオプションは非推奨であり、通常バックエンドはこの関数の外で変更するべきです）。

さらなるプロットの更新に使用できるオブジェクトを返します。
```
