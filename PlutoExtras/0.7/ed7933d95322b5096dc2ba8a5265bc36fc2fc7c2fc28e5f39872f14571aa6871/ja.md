```
StringOnEnter(default::AbstractString)
```

`@bind`と一緒に使用することで、文字列を出力として提供できるPlutoウィジェットを作成します。

PlutoUIのカスタム「TextField」とは異なり、Enterキーを押すかウィジェットのフォーカスを外すときにのみバインドの更新がトリガーされます（[`Editable`](@ref)に似ています）。

HTMLでレンダリングされると、ウィジェットのテキストは暗い黄色の背景で表示されます。

![868c1c6e-8731-4465-959e-58cf551b9f61](https://github.com/disberd/PlutoExtras.jl/assets/12846528/782360f2-595a-4bbe-9769-5ddfaa144611)
