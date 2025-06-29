---

`ParametricMCP`をコンパイルするための主なコンストラクタ

位置引数:

  * `f`: 決定変数 `z` の長さ `n` のベクトルと、サイズ `parameter_dimension` のパラメータベクトル `θ` をマッピングする `f(z, θ)` として呼び出せる関数で、長さ `n` のベクトル出力を返します。
  * `lower_bounds`: 決定変数 `z` に対する要素ごとの下限の長さ `n` のベクトル。
  * `upper_bounds`: 決定変数 `z` に対する要素ごとの上限の長さ `n` のベクトル。
  * `parameter_dimension`: `f` におけるパラメータベクトル `θ` のサイズ。

キーワード引数:

  * `[backend]`: `f` と PATH に必要なヤコビ行列のコールバックをコンパイルするために使用されるバックエンド（`SymbolicTracingUtils`から）。`SymbolicsBackend`（デフォルト）は若干柔軟性があります。`FastDifferentiationBackend` はコンパイル時間を短縮し、場合によっては実行時間を短縮します。
  * `compute_sensitivities`: 感度計算に必要なコールバックをコンパイルするかどうか。
  * `[problem_size]`: 決定変数の数。提供されていない場合、かつ `lower_bounds` または `upper_bounds` がベクトルである場合、問題のサイズはこれらのベクトルの長さから推測されます。

注意: このコンストラクタは、関連する低レベル関数をコンパイルするためにシンボリックトレースを使用します。したがって、`f` はシンボリック評価をサポートする十分に一般的な方法で実装されている必要があります。それが不可能または非現実的な場合でも、低レベルコンストラクタを使用して `ParametricMCP` を生成することは可能です。ただし、一般的には、この便利なコンストラクタの使用が推奨されます。
