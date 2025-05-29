```
RAGConfig <: AbstractRAGConfig
```

RAGのデフォルト設定です。デフォルトのコンポーネントとして`SimpleIndexer`、`SimpleRetriever`、および`SimpleGenerator`を使用します。`airag`の最初の引数として提供されます。

コンポーネントをカスタマイズするには、RAGパイプラインの各ステップの対応するフィールドを置き換えます（例：利用可能なオプションを見つけるには`subtypes(AbstractIndexBuilder)`を使用します）。
