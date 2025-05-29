```
getndof(model|Element)
getndof(model|Element,class)
getndof(model|Element,(class1,class2,[,...]))
```

ここで `class` は `:X`, `:U`, `:A` のいずれかであり、変数 `model` または型 `Element` の指定されたdofクラスの数を取得します（デフォルト：すべてのクラス）。

参照: [`describe`](@ref)
