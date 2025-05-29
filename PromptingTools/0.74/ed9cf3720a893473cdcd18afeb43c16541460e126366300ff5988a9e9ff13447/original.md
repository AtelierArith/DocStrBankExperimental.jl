```
recursive_splitter(text::AbstractString, separators::Vector{String}; max_length::Int=35000) -> Vector{String}
```

Split a given string `text` into chunks recursively using a series of separators, with each chunk having a maximum length of `max_length` (if it's achievable given the `separators` provided).  This function is useful for splitting large documents or texts into smaller segments that are more manageable for processing, particularly for models or systems with limited context windows.

It was previously known as `split_by_length`.

This is similar to Langchain's [`RecursiveCharacterTextSplitter`](https://python.langchain.com/docs/modules/data_connection/document_transformers/recursive_text_splitter). To achieve the same behavior, use `separators=["\n\n", "\n", " ", ""]`.

# Arguments

  * `text::AbstractString`: The text to be split.
  * `separators::Vector{String}`: An ordered list of separators used to split the text. The function iteratively applies these separators to split the text. Recommend to use `["\n\n", ". ", "\n", " "]`
  * `max_length::Int`: The maximum length of each chunk. Defaults to 35,000 characters. This length is considered after each iteration of splitting, ensuring chunks fit within specified constraints.

# Returns

`Vector{String}`: A vector of strings, where each string is a chunk of the original text that is smaller than or equal to `max_length`.

# Usage Tips

  * I tend to prefer splitting on sentences (`". "`) before splitting on newline characters (`"\n"`) to preserve the structure of the text.
  * What's the difference between `separators=["\n"," ",""]` and `separators=["\n"," "]`?  The former will split down to character level (`""`), so it will always achieve the `max_length` but it will split words (bad for context!) I prefer to instead set slightly smaller `max_length` but not split words.

# How It Works

  * The function processes the text iteratively with each separator in the provided order. It then measures the length of each chunk and splits it further if it exceeds the `max_length`. If the chunks is "short enough", the subsequent separators are not applied to it.
  * Each chunk is as close to `max_length` as possible (unless we cannot split it any further, eg, if the splitters are "too big" / there are not enough of them)
  * If the `text` is empty, the function returns an empty array.
  * Separators are re-added to the text chunks after splitting, preserving the original structure of the text as closely as possible. Apply `strip` if you do not need them.
  * The function provides `separators` as the second argument to distinguish itself from its single-separator counterpart dispatch.

# Examples

Splitting text using multiple separators:

```julia
text = "Paragraph 1\n\nParagraph 2. Sentence 1. Sentence 2.\nParagraph 3"
separators = ["\n\n", ". ", "\n"] # split by paragraphs, sentences, and newlines (not by words)
chunks = recursive_splitter(text, separators, max_length=20)
```

Splitting text using multiple separators - with splitting on words:

```julia
text = "Paragraph 1\n\nParagraph 2. Sentence 1. Sentence 2.\nParagraph 3"
separators = ["\n\n", ". ", "\n", " "] # split by paragraphs, sentences, and newlines, words
chunks = recursive_splitter(text, separators, max_length=10)
```

Using a single separator:

```julia
text = "Hello,World," ^ 2900  # length 34900 characters
chunks = recursive_splitter(text, [","], max_length=10000)
```

To achieve the same behavior as Langchain's `RecursiveCharacterTextSplitter`, use `separators=["\n\n", "\n", " ", ""]`.

```julia
text = "Paragraph 1\n\nParagraph 2. Sentence 1. Sentence 2.\nParagraph 3"
separators = ["\n\n", "\n", " ", ""]
chunks = recursive_splitter(text, separators, max_length=10)

```
