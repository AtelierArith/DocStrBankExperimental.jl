```
KeywordsIndexer <: AbstractIndexBuilder
```

Keyword-based index (BM25) to be returned by `build_index`.

It uses `TextChunker`, `KeywordsProcessor`, and `NoTagger` as default chunker, processor, and tagger.
