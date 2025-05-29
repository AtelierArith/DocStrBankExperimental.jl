```
read_template(data_path::String)
```

Reads a prompt template from a JSON file specified by `data_path`. The function parses the JSON data and constructs a `PromptTemplate` object containing metadata, system, and user messages. TODO: validate the JSON data against a schema to ensure it is valid before parsing.

# Arguments

  * `data_path::String`: The path to the JSON file containing the prompt template.

# Returns

  * `PromptTemplate`: A `PromptTemplate` structure encapsulating the metadata, system, and user messages.

# Raises

  * `ErrorException`: if the template does not match the specification format.
