```
words(languages...; all)
```

言語の単語をソートされた `Vector{String}` としてリストします。

リストは不完全であり、その正確な内容は変更される可能性があります。 `all=true` を設定すると、すべての単語を含める努力をしますが、一部の非単語も含まれる可能性があります。

言語は ISO コード、名前、または英語名で照会でき、大文字と小文字は区別されません。

現在サポートされている言語は次のとおりです：

  * 英語: "english", "eng", "en"
  * スペイン語: "spanish", "español", "spa", "es"
  * ポルトガル語: "portuguese", "português", "por", "pt"
  * フランス語: "french", "français", "fre", "fr"
  * イタリア語: "italian", "italiano", "ita", "it"
  * ドイツ語: "german", "deutsch", "deu", "de"
  * オランダ語: "dutch", "nederlands", "nld", "nl"

多言語リストがサポートされています。たとえば、`words("english", "spanish")` は、英語とスペイン語の両方の単語を含むソートされたリストを返します。

# 例

```julia-repl
julia> words("english")
257874-element Vector{String}:
 "Aani"
 "Aaron"
 "Aaronic"
 ⋮
 "zymurgy"
 "zythem"
 "zythum"

julia> words("es", "en")
257874-element Vector{String}:
 "Aani"
 "Aaron"
 "Aaronic"
 ⋮
 "útero"
 "útil"
 "útiles"

julia> rand(words("EnGLiSH", "EspañoL"; all=true), 6)
6-element Vector{String}:
 "Upham"
 "asentir"
 "butcher"
 "fireworm"
 "cirrolite"
 "revocable"
```
