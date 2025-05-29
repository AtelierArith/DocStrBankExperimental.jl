`@quasiabstract expression`

*クワジ抽象*型を作成します。

このマクロは、（可変または不変の）構造体を定義する式を受け取り、次の2つの新しい型定義のコードを出力します：

  * 入力構造体と同じ名前と（指定されている場合）スーパタイプを持つ抽象型；
  * 上記で定義された抽象型をサブタイプとする、名前の接頭辞が `Concrete_` の具体的な構造体定義。

型間の関係により、抽象型に関連付けられた単一の具体的な型が存在することが保証されるため、抽象型を使用してメソッド引数を注釈付けし、関連付けられた具体的な型またはそのサブタイプ（先祖のすべてのフィールド名と型を共有する）を受け取ることができます。

*クワジ抽象*型に関連付けられた具体的な型は、`concretetype`関数を使用して取得できます。 `Concrete_`接頭辞は、マクロに2番目のシンボル引数を渡すことでカスタマイズできます。

これらの新しく定義された型は、具体的なサブタイピングを簡単に実装できるようにします：オブジェクトの構築とメソッド引数の注釈付けの両方に*クワジ抽象*型名を単純に使用します。

# 例：

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
