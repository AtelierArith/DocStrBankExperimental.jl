Index for accessing a comment associated with a header keyword or COMMENT entry.

Example:

```julia
img = AstroImage(randn(10,10))
img["ABC"] = 1
img["ABC", Comment] = "A comment describing this key"

push!(img, Comment, "The purpose of this file is to demonstrate comments")
img[Comment] # ["The purpose of this file is to demonstrate comments"]
```
