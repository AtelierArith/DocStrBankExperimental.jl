```
cast_document(input_path, output_path=input_path; format="gfm+attributes")
```

For each `julia {cast="true"}` code-block in the input document, generates a gif executing that code in a REPL, saves it to `joinpath(dirname(output_path), "assets")` and inserts it as an image following the code-block, writing the resulting document to `output_path`.

The default `format` is Github-flavored markdown. Specify the `format` keyword argument to choose an alternate pandoc-supported format (see [https://pandoc.org/MANUAL.html#general-options](https://pandoc.org/MANUAL.html#general-options)). This has only been tested with Github-flavored markdown, but theoretically should work with any pandoc format.

Returns the number of gifs generated.

!!! warning
    This function relies on parsing the document using pandoc and roundtripping through the pandoc AST. This can result in unexpected modifications to the document.

    It is recommended to check your document into source control before running this function, or specifying an `output_path` that is different from the input path, in order to assess the results.

