```
File(parent, name, value=NoValue())
```

#### フィールド:

  * `parent::Union{FileTree, Nothing}` – 親ノード。ルートノードの場合は `nothing`。
  * `name::String` – ルートの名前。
  * `value::Any` – ノードの値。値が存在しない場合は、`NoValue()` センティネル値。
