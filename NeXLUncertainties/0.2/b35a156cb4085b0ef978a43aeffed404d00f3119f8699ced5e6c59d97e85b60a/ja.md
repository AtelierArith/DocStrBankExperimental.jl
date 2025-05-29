```
LabeledValues
```

`LabeledValues`オブジェクトは、`Label`付きの値（`Float64`）の配列を効率的に扱う方法を表します。各値は`Label`を介してインデックス付けされるため、`Vector`に格納する場合はO(N)ですが、`Dict`に`Label`と値を格納する場合はO(1)です。しかし、`Dict`に格納すると、保持したい順序が失われます。`LabeledValues`は、ラベルの順序を保持しながらO(1)です。
