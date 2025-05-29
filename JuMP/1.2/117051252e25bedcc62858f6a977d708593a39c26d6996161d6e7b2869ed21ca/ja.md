```
latex_formulation(model::AbstractModel)
```

`model`を型でラップして、IJuliaのようなノートブックやDocumenterで`text/latex`としてきれいに表示できるようにします。

モデルをレンダリングするには、セルの最後に`latex_formulation(model)`を記述するか、関数内からモデルの表示を強制するために`display(latex_formulation(model))`を呼び出します。
