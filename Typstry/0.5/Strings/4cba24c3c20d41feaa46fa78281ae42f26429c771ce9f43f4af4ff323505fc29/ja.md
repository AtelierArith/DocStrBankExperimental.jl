```
show_typst(io, x)
```

Juliaの設定と`IOContext`によって提供されるTypstパラメータでTypst形式で印刷します。

カスタムタイプのためにこの関数を実装して、そのTypstフォーマットを指定します。設定はJuliaで使用される値であり、その型は設定によって異なります。パラメータはTypst関数に直接渡され、Typstでの名前と同じ名前の[`TypstString`](@ref)でなければなりませんが、ダッシュはアンダースコアに置き換えられます。設定にはそれぞれデフォルト値があり、パラメータのデフォルト値はTypst関数によって処理されます。`block`のような一部の設定はパラメータに対応していますが、Juliaでも使用される場合があります。

設定とパラメータに関する追加情報については、[`context`](@ref)および[Typst Documentation](https://typst.app/docs/)も参照してください。

!!! info
    特にコンテナなどの一部のタイプは、[`show(::IO, ::MIME"text/typst", ::Typst)`](@ref)を呼び出して値をフォーマットすることがあり、追加の設定やパラメータを使用する場合があります。


!!! warning
    この関数のメソッドは不完全です。欠落しているメソッドについては、問題を報告するかプルリクエストを作成してください。


| タイプ                                             | 設定                                       | パラメータ                                                   |
|:----------------------------------------------- |:---------------------------------------- |:------------------------------------------------------- |
| `AbstractArray`                                 | `:block`, `:depth`, `:mode`, `:tab_size` | `:delim`, `:gap`                                        |
| `AbstractChar`                                  |                                          |                                                         |
| `AbstractFloat`                                 | `:mode`                                  |                                                         |
| `AbstractMatrix`                                | `:block`, `:depth`, `:mode`, `:tab_size` | `:augment`, `:column_gap`, `:delim`, `:gap`, `:row_gap` |
| `AbstractString`                                |                                          |                                                         |
| `Bool`                                          | `:mode`                                  |                                                         |
| `Complex{Bool}`                                 | `:block`, `:mode`, `:parenthesize`       |                                                         |
| `Complex`                                       | `:block`, `:mode`, `:parenthesize`       |                                                         |
| `Irrational`                                    | `:mode`                                  |                                                         |
| `Nothing`                                       | `:mode`                                  |                                                         |
| `OrdinalRange{<:Integer, <:Integer}`            | `:mode`                                  |                                                         |
| `Rational`                                      | `:block`, `:mode`, `:parenthesize`       |                                                         |
| `Regex`                                         | `:mode`                                  |                                                         |
| `Signed`                                        | `:mode`                                  |                                                         |
| `StepRangeLen{<:Integer, <:Integer, <:Integer}` | `:mode`                                  |                                                         |
| `Tuple`                                         | `:block`, `:depth`, `:mode`, `:tab_size` | `:delim`, `:gap`                                        |
| `Typst`                                         |                                          |                                                         |
| `TypstString`                                   |                                          |                                                         |
| `TypstText`                                     | `:mode`                                  |                                                         |
| `Unsigned`                                      | `:mode`                                  |                                                         |
| `VersionNumber`                                 | `:mode`                                  |                                                         |
| `Docs.HTML`                                     | `:block`, `:depth`, `:mode`, `:tab_size` |                                                         |
| `Docs.Text`                                     | `:mode`                                  |                                                         |
| `Dates.Date`                                    | `:mode`, `:indent`                       |                                                         |
| `Dates.DateTime`                                | `:mode`, `:indent`                       |                                                         |
| `Dates.Period`                                  | `:mode`, `:indent`                       |                                                         |
| `Dates.Time`                                    | `:mode`, `:indent`                       |                                                         |

```
