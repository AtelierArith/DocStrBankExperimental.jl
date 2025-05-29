LSystem（リンデンマイヤーシステム）とは、再帰的なパターンを定義できるルールのセットです。

次のようにL-Systemを定義できます：

```
koch = LSystem(["F" => "F+F--F+F"], "F")
```

そして、次のようにLuxorを使って描画できます：

```
drawLSystem(koch, forward=30, turn=45, iterations=6)
```

詳細については `help?> LSystem` および `help?> ?>LSystem` を参照してください。
