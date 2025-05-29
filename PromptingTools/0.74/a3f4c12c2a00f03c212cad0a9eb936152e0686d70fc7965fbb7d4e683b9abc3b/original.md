```
recursive_splitter(text::String; separator::String=" ", max_length::Int=35000) -> Vector{String}
```

Split a given string `text` into chunks of a specified maximum length `max_length`.  This is particularly useful for splitting larger documents or texts into smaller segments, suitable for models or systems with smaller context windows.

There is a method for dispatching on multiple separators, `recursive_splitter(text::String, separators::Vector{String}; max_length::Int=35000) -> Vector{String}` that mimics the logic of Langchain's `RecursiveCharacterTextSplitter`.

# Arguments

  * `text::String`: The text to be split.
  * `separator::String=" "`: The separator used to split the text into minichunks. Defaults to a space character.
  * `max_length::Int=35000`: The maximum length of each chunk. Defaults to 35,000 characters, which should fit within 16K context window.

# Returns

`Vector{String}`: A vector of strings, each representing a chunk of the original text that is smaller than or equal to `max_length`.

# Notes

  * The function ensures that each chunk is as close to `max_length` as possible without exceeding it.
  * If the `text` is empty, the function returns an empty array.
  * The `separator` is re-added to the text chunks after splitting, preserving the original structure of the text as closely as possible.

# Examples

Splitting text with the default separator (" "):

```julia
text = "Hello world. How are you?"
chunks = recursive_splitter(text; max_length=13)
length(chunks) # Output: 2
```

Using a custom separator and custom `max_length`

```julia
text = "Hello,World," ^ 2900 # length 34900 chars
recursive_splitter(text; separator=",", max_length=10000) # for 4K context window
length(chunks[1]) # Output: 4
```
