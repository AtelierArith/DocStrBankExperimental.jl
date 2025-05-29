Create a `TopicModel` of text in corpus `c` with `k` topics. Optional parameters:

  * `alpha` is the `TextAnalysis` package's α. From its documentation: "The hyperparameter for topic distribution per document. α<1 yields a sparse topic mixture for each document. α>1 yields a more uniform topic mixture for each document."
  * `beta`  is the `TextAnalysis` package's β. "The hyperparameter for word distribution per topic. β<1 yields a sparse word mixture for each topic. β>1 yields a more uniform word mixture for each topic."
  * `iters` Number of iterations.
  * `stopwords` List of terms to omit from the model.
  * `doclabels` Vector of strings identifying each document.  If `doclabels` is empty, string values of the document's URN are used.  The length of `doclabels` must equal the number of documents in the corpus, and values must be unique.
