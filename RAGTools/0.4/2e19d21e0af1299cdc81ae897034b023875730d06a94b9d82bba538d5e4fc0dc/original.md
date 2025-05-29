```
RAGConfig <: AbstractRAGConfig
```

Default configuration for RAG. It uses `SimpleIndexer`, `SimpleRetriever`, and `SimpleGenerator` as default components. Provided as the first argument in `airag`.

To customize the components, replace corresponding fields for each step of the RAG pipeline (eg, use `subtypes(AbstractIndexBuilder)` to find the available options).
