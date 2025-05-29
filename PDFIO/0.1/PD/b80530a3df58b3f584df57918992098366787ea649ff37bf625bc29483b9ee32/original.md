```
    pdDocHasSignature(doc::PDDoc) -> Bool
```

Returns `true` when the document has at least one signature field.

This does not mean there is an actual digital signature embedded in the document. A PDF document can be signed and content can be approved by one or more reviewers. Signature fields are placeholders for storing and rendering such information.

# Example

```
julia> pdDocHasSignature(doc)
true
```
