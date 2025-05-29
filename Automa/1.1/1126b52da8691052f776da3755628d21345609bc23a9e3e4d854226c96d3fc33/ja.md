```
generate_reader(funcname::Symbol, machine::Automa.Machine; kwargs...)
```

`machine`から`funcname`という名前のストリーミングリーダー関数を生成します。

生成された関数は、最初の引数として渡されたストリームからデータを消費し、データバッファを満たすためにマシンを実行します。

この関数は、生成された関数の式オブジェクトを返します。ユーザーは、生成された関数が必要なモジュールでそれを評価する必要があります。

# キーワード引数

  * `arguments`: `funcname`が受け取る追加の引数（デフォルト: `()`）。生成された関数のデフォルトのシグネチャは`(stream::TranscodingStream,)`ですが、このキーワード引数を使用してシグネチャにさらに引数を供給することが可能です。
  * `context`: Automaのコードジェネレーター（デフォルト: `Automa.CodeGenContext()`）。
  * `actions`: アクションコードの辞書（デフォルト: `Dict{Symbol,Expr}()`）。
  * `initcode`: 初期化コード（デフォルト: `:()`）。
  * `loopcode`: ループコード（デフォルト: `:()`）。
  * `returncode`: 戻りコード（デフォルト: `:(return cs)`）。
  * `errorcode`: `loopcode`の後に`cs < 0`の場合に実行される（デフォルトのエラーメッセージ）

この関数のソースコードを参照して、生成されたコードがどのように見えるかを確認してください。
