```
FileTree(parent, name, children, value)
```

#### フィールド:

  * `parent::Union{FileTree, Nothing}` – 親ノード。ルートノードの場合は `nothing`。
  * `name::String` – ルートの名前。
  * `children::Vector` – 子ノード
  * `value::Any` – ノードの値。値が存在しない場合は、`NoValue()` センティナル値。

    FileTree(tree::FileTree; parent, name, children, value)

すべてのフィールドを `tree` からコピーしますが、キーワード引数として提供されたフィールドは使用します。

```
FileTree(dirname::String)
```

現在の作業ディレクトリのディスクからディレクトリを反映する `FileTree` を構築します。
