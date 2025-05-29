```
SemCor()
```

コーパスの遅延読み込みのためのSemCorインスタンスを作成します。

# 使用例

```jldoctest
julia> corp = load(SemCor())
Channel{CorpusLoaders.Document{Array{Array{Array{CorpusLoaders.TaggedWord,1},1},1},String}}(sz_max:16,sz_curr:16)

julia> index = Dict{String, Vector{Vector{String}}}()
Dict{String,Array{Array{String,1},1}} with 0 entries

julia> for sentence in flatten_levels(corp, (!lvls)(SemCor, :sent, :word))
           multisense_words = filter(x->x isa SenseAnnotatedWord,  sentence)
           context_words = word.(sentence)
           for target in multisense_words
               word_sense = sensekey(target)
               uses = get!(Vector{Vector{String}}, index, word_sense)
               push!(uses, context_words)
           end
       end

julia> index["abandon%1:07:00::"]
1-element Array{Array{String,1},1}:
 String["in", "his", "motherland", ";", "in", "the", "spacious", "hunting_grounds", "of", "``"  …  ",", "color", ",", "dance", ",", "design", ",", "and", "thought", "."]

julia> index["abandon%2:38:00::"]
2-element Array{Array{String,1},1}:
 String["Jonathan", "wrote", "grimly", "of", "the", "destruction", "of", "Harpers_Ferry", "before", "they"  …  "First_Brigade", "had", "destroyed", "all", "the", "rolling_stock", "of", "the", "B_+_O_Railroad", "."]
 String["The", "expense", "of_this", "type", "of", "organization", "in", "religious", "life", ","  …  "in", "congregations", "illumines", "the", "nature", "of", "the", "Protestant", "development", "."]

```

SemCorは古典的な意味注釈コーパスです。

文書、段落、文、単語の構造を持っています。

単語は品詞でタグ付けされているか、完全なレマ、品詞、センスキーでタグ付けされています。

単語を取得するためのword関数と、センスキーを抽出するためのsensekey関数を公開しています。

テキストはWordNet 1.6のセンスで意味的に注釈されており（プリンストン大学で作成）、WordNet 1.7、WordNet 1.7.1、WordNet 2.0、WordNet 2.1、WordNet 3.0に自動的にマッピングされています:  SemCor 1.7  SemCor 1.7.1  SemCor 2.0  SemCor 2.1  SemCor 3.0

コーパスを使用する場合は、以下の出版物を引用してください:         George A. Miller, Claudia Leacock, Randee Tengi, and Ross T. Bunker. (1993). "A Semantic Concordance." In: Proceedings of the 3 DARPA Workshop on Human Language Technology.
