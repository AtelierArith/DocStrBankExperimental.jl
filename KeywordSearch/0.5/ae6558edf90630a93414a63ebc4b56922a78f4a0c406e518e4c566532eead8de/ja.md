```
word_boundary(Q::AbstractQuery) -> AbstractQuery
```

周囲のテキストとハイフンでつながったり結合されたりしない単語やフレーズを保証します。

## 例

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
