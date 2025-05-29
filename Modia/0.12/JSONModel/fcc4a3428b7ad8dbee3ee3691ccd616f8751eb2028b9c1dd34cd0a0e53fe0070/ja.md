```
json = modelToJSON(model; expressionsAsStrings=true)
```

モデルをJSONとしてエンコードします。式は文字列またはASTとして保存できます。

  * `model`: モデル（宣言と方程式）
  * `expressionsAsStrings`: 文字列として保存されたJulia式または辞書として保存されたExpr構造体
  * `return JSON string for the model`
