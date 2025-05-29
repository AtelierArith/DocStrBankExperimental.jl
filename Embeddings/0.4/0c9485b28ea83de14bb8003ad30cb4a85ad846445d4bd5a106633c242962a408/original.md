```
load_embeddings(EmbeddingSystem, [embedding_file|default_file_number])
load_embeddings(EmbeddingSystem{:lang}, [embedding_file|default_file_number])
```

Loaded the embeddings from a embedding file. The embeddings should be of the type given by the Embedding system.

If the `embedding file` is not provided, a default embedding file will be used. (It will be automatically installed if required). EmbeddingSystems have a language type parameter. For example `FastText_Text{:fr}` or `Word2Vec{:en}`, if that language parameter is not given it defaults to English. (I am sorry for the poor state of the NLP field that many embedding formats are only available pretrained in English.) Using this the correct  default embedding file will be installed for that language. For some languages and embedding systems there are multiple possible files. You can check the list of them using for example `language_files(FastText_Text{:de})`. The first is nominally the most popular, but if you want to default to another you can do so by setting the `default_file_num`.

### Keyword Arguments:

  * `max_vocab_size` an integer, it specifies the maximum number of words to load (most formats are sorted by frequency so this keeps the the most common words). Default is to keep all of them
  * `keep_words=Set()` if a non-empty set of words is provided, then only word embeddings for words from that list are loaded. Otherwise (default) all words are loaded.

### Returns an `Embeddings` object.

This has 2 fields.

  * `embeddings` is a matrix, each column is the embedding for a word.
  * `vocab` is a vector of strings, ordered as per the columns of `embeddings`, such that the first string in vocab is the first column of `embeddings` etc

We do not include a method for getting the index of a column from a word. This is trivial to define in code (`vocab2ind(vocab)=Dict(word=>ii for (ii,word) in enumerate(vocab))`), and you might like to be doing this in a more consistant way, e.g using [MLLabelUtils.jl](https://github.com/JuliaML/MLLabelUtils.jl), or you might like to build a much faster Dict solution on top of [InternedStrings.jl](https://github.com/JuliaString/InternedStrings.jl)

```
