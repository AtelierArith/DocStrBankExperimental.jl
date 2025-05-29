```
SimpleIndexer <: AbstractIndexBuilder
```

Default implementation for `build_index`.

It uses `TextChunker`, `BatchEmbedder`, and `NoTagger` as default chunker, embedder, and tagger.
