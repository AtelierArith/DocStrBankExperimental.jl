```julia
decrypt_solitaire(string::AbstractString, initialDeck::AbstractVector{T}) where {T <: Integer}
```

与えられた暗号文をソリティア暗号に従って復号化します。キーは、カードが1から54（2つのジョーカーが53、54）であるベクター初期デッキとして与えることも、文字列として与えることもできます。キーが文字列の場合、シュナイアのキーイングアルゴリズムがデッキのキーに使用されます。

---

### 例

```julia
julia> decrypt_solitaire("EXKYI ZSGEH UNTIQ", collect(1:54)) # as per https://www.schneier.com/code/sol-test.txt
"aaaaaaaaaaaaaaa"
```
