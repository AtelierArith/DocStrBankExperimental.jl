コンパイルの成功と失敗に関連するさまざまなメトリックを追跡するために使用されるオブジェクトで、後での内省のために使用されます。

たとえば、すべてまたは少なくとも特定の数のトレースが正常にコンパイルされたことをテストまたはアサートしたい場合があります。

公開フィールド：

  * `succeeded`: 正常にコンパイルされたステートメントの数。
  * `failed`: コンパイルに失敗したステートメントの数。
  * `skipped`: コンパイルの制限により回避されたステートメントの数。これは非常にまれで、オーバーロードされた `Vararg` または非特殊化された引数に関連しています。
  * `total`: 処理されたステートメントの数。これは他の3つのフィールドの合計です。
