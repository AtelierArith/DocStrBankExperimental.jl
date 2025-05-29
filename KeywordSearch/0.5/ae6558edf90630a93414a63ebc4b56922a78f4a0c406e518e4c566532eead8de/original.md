```
word_boundary(Q::AbstractQuery) -> AbstractQuery
```

Ensures that a word or phrase is not hyphenated or conjoined with the surrounding text.

## Example

```jldoctest
julia> using Test

julia> query = Query("word")
Query("word")

julia> @test match(query, Document("This matchesword ")) !== nothing
Test Passed

julia> @test match(word_boundary(query), Document("This matches word.")) !== nothing
Test Passed

julia> @test match(word_boundary(query), Document("This matches word ")) !== nothing
Test Passed

julia> @test match(word_boundary(query), Document("This matches word\nNext line")) !== nothing
Test Passed

julia> @test match(word_boundary(query), Document("This doesn't matchword ")) === nothing
Test Passed

```
