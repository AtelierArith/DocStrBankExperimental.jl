`@quasiabstract expression`

Create a *quasi abstract* type.

This macro accepts an expression defining a (mutable or immutable) structure, and outputs the code for two new type definitions:

  * an abstract type with the same name and (if given) supertype of the input structure;
  * a concrete structure definition with name prefix `Concrete_`, subtyping the abstract type defined above.

The relation between the types ensure there will be a single concrete type associated to the abstract one, hence you can use the abstract type to annotate method arguments, and be sure to receive the associated concrete type, or one of its subtypes (which shares all field names and types of the ancestors).

The concrete type associated to an *quasi abstract* type can be retrieved with the `concretetype` function.  The `Concrete_` prefix can be customized passing a second symbol argument to the macro.

These newly defined types allows to easily implement concrete subtyping: simply use the *quasi abstract* type name for both object construction and to annotate method arguments.

# Example:

```julia-repl
julia> @quasiabstract struct Book
    title::String
    author::String
end
julia> Base.show(io::IO, b::Book) = println(io, "$(b.title) (by $(b.author))")
julia> Base.print(b::Book) = println("In a hole in the ground there lived a hobbit...")
julia> author(b::Book) = b.author

julia> @quasiabstract struct PaperBook <: Book
    number_of_pages::Int
end
julia> pages(book::PaperBook) = book.number_of_pages

julia> @quasiabstract struct Edition <: PaperBook
    year::Int
end
julia> year(book::Edition) = book.year

julia> println(fieldnames(concretetype(Edition)))
(:title, :author, :number_of_pages, :year)

julia> book = Edition("The Hobbit", "J.R.R. Tolkien", 374, 2013)

julia> print(author(book), ", ", pages(book), " pages, Ed. ", year(book))
J.R.R. Tolkien, 374 pages, Ed. 2013

julia> print(book)
In a hole in the ground there lived a hobbit...

julia> @assert isquasiconcrete(typeof(book))

julia> @assert isquasiabstract(supertype(typeof(book)))

julia> @assert concretetype(supertype(typeof(book))) === typeof(book)
```
