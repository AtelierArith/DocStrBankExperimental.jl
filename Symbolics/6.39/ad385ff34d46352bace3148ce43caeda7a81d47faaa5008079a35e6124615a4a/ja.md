```
build_function(ex, args...;
               expression = Val{true},
               target = JuliaTarget(),
               parallel=nothing,
               kwargs...)
```

Symbolics `Num` から数値的に使用可能な関数を生成します。

引数:

  * `ex`: コンパイルする `Num`
  * `args`: 関数の引数
  * `expression`: コードを生成するか、コンパイルされた形式を生成するか。デフォルトでは `expression = Val{true}` で、これは関数のコードが返されることを意味します。`Val{false}` の場合、返される値はコンパイルされたものになります。

キーワード引数:

  * `target`: コンパイルプロセスの出力ターゲット。可能なオプションは次のとおりです:

      * `JuliaTarget`: Julia 関数を生成します
      * `CTarget`: C 関数を生成します
      * `StanTarget`: Stan 確率的プログラミング言語でコンパイルするための関数を生成します
      * `MATLABTarget`: MATLAB および Octave 環境で使用するための匿名関数を生成します
  * `parallel`: 生成された関数で使用する並列性の種類。デフォルトは `SerialForm()` で、これは `ex` が単一の式または <= 1500 の非ゼロ式を含む配列の場合、並列性がないことを意味します。`ex` が > 1500 の非ゼロ式の配列の場合、`ShardedForm(80, 4)` が使用されます。`ShardedForm` についての詳細は以下を参照してください。並列形式はエクスポートされていないため、`Symbolics.SerialForm()` のように選択する必要があります。選択肢は次のとおりです:

      * `SerialForm()`: シリアル実行。
      * `ShardedForm(cutoff, ncalls)`: 出力関数を、最大 `cutoff` 数の出力 `rhss` を含むサブ関数に分割します。これらのサブ関数は、*build*function が返すトップレベル関数によって呼び出されます。これにより、生成された関数のコンパイル時間を短縮できます。
      * `MultithreadedForm()`: スタティックスプリットによるマルチスレッド実行で、スレッドごとに式の数を均等に分割します。
  * `fname`: 一部のターゲットでターゲット空間内の関数の名前として使用されます。

すべてのビルドターゲットが完全なコンパイルインターフェースをサポートしているわけではありません。詳細については、個々のターゲットのドキュメントを確認してください。
