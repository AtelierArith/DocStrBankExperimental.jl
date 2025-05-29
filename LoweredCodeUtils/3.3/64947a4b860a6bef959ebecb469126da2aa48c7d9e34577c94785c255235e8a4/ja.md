```
ret = methoddef!([interp::Interpreter=RecursiveInterpreter()], signatures, frame; define=true)
```

メソッド定義のシグネチャを計算します。`frame.pc`は`:method`式を指している必要があります。終了時に、新しいシグネチャが`signatures`に追加されます。

いくつかの可能な戻り値があります：

```
pc, pc3 = ret
```

は典型的な戻り値です。`pc`は次に実行されるステートメントを指すか、`frame`にさらなるステートメントがない場合は`nothing`になります。`pc3`は3引数の`:method`式を指します。

あるいは、

```
pc = ret
```

は「空のメソッド」式、例えば`:(function foo end)`の場合に発生します。`pc`は`nothing`になります。

デフォルトでは、メソッドは定義（評価）されます。これを防ぐには、`define=false`を設定します。これは、すでに評価されたコードからシグネチャを単に抽出する場合に推奨されます。
