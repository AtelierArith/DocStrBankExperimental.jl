NBIncludeモジュールを使用すると、IJulia JupyterノートブックからJuliaコードを含めて実行できます。 `include("myfile.jl")`に類似して、次のようにします。

```
using NBInclude
@nbinclude("myfile.ipynb")
```

これにより、ノートブック`myfile.ipynb`からJuliaコードが含まれます。 `include`と同様に、最後に評価された式の値が返されます。
