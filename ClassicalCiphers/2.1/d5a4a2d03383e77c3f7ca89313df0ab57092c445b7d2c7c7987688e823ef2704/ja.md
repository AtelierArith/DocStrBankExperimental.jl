```julia
encrypt_solitaire(string::AbstractString, initialDeck::AbstractVector{T}) where {T <: Integer}
```

与えられた平文をソリティア暗号に従って暗号化します。キーは、カードが1から54（2つのジョーカーが53、54）であるベクター初期デッキとして、または文字列として与えることができます。キーが文字列の場合、シュナイアのキー生成アルゴリズムがデッキのキーに使用されます。

---

### 例

```julia
julia> encrypt_solitaire("Hello, World!", "crypto")
"GRNNQISRYA"
```
