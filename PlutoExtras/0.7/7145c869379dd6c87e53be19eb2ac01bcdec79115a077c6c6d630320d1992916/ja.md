```
Editable(x::Bool[, true_string="true", false_string="false")
```

Boolean値を含むPlutoウィジェットを作成します。

表示されるHTMLは、真の場合にカスタム文字列`true_string`を表示し、偽の場合に`false_string`を表示する緑の背景を持つspanを作成します。提供されていない場合、第二引数`true_string`は"true"に、第三引数は"false"にデフォルト設定されます。

ウィジェットは、クリックするとボンドの更新をトリガーします。

![991b712a-d62d-4036-b096-fe0fc52c9b25](https://github.com/disberd/PlutoExtras.jl/assets/12846528/f12e3bc3-f78c-45b5-b5fd-06f2083fc5c4)
