`@forward(sender, receiver, ekws...)`

メソッドを転送するためのJuliaコードを評価します。構文は`forward`関数と全く同じです。

# 例:

```julia-repl
julia> struct Book
    title::String
    author::String
end
julia> Base.show(io::IO, b::Book) = println(io, "$(b.title) (by $(b.author))")
julia> Base.print(b::Book) = println("In a hole in the ground there lived a hobbit...")
julia> author(b::Book) = b.author

julia> struct PaperBook
    b::Book
    number_of_pages::Int
end
julia> @forward((PaperBook, :b), Book)
julia> pages(book::PaperBook) = book.number_of_pages

julia> struct Edition
    b::PaperBook
    year::Int
end
julia> @forward((Edition, :b), PaperBook)
julia> year(book::Edition) = book.year

julia> book = Edition(PaperBook(Book("The Hobbit", "J.R.R. Tolkien"), 374), 2013)

julia> print(author(book), ", ", pages(book), " pages, Ed. ", year(book))
J.R.R. Tolkien, 374 pages, Ed. 2013

julia> print(book)
In a hole in the ground there lived a hobbit...
```
