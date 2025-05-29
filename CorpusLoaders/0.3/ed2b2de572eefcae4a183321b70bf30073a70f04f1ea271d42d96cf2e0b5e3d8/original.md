```
SemCor()
```

Creates a SemCor instance for lazy loading the corpus.

# Example Usage

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

SemCor is a classical Sense Annotated Corpus.

It has a structure of documents, paragraphs, sentences, words.

The words are either tagged with part of speech, or tagged with full lemma, part of speech and sensekey.

We expose the word function to get back the words, and the sensekey function to extract the sense key.

Texts semantically annotated with WordNet 1.6 senses (created at Princeton University), and automatically mapped to WordNet 1.7, WordNet 1.7.1, WordNet 2.0, WordNet 2.1, WordNet 3.0 to get:  SemCor 1.7  SemCor 1.7.1  SemCor 2.0  SemCor 2.1  SemCor 3.0

Please cite the following publication if you use the corpora:         George A. Miller, Claudia Leacock, Randee Tengi, and Ross T. Bunker. (1993). "A Semantic Concordance." In: Proceedings of the 3 DARPA Workshop on Human Language Technology.
