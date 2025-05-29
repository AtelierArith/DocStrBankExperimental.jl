# Readability.jl

Julia package for computing readability scores.

## Functions:

  * `Readability.ari(text::String)::Int`
  * `Readability.characters(text::String)::Int`
  * `Readability.characters_per_word(text::String)::Number`
  * `Readability.coleman_liau(text::String)::Number`
  * `Readability.complex_words(text::String)::Int`
  * `Readability.dale_chall(text::String)::Number`
  * `Readability.difficult_words(text::String, word_list::String)::Int`
  * `Readability.flesch_kincaid_grade_level(text::String)::Float64`
  * `Readability.flesch_reading_ease_score(text::String)::Float64`
  * `Readability.gunning_fog(text::String)::Number`
  * `Readability.lines(text::String)::Int`
  * `Readability.paragraphs(text::String)::Int`
  * `Readability.polysyllabic_words(text::String)::Int`
  * `Readability.reading_time(text::String; wpm::Number=183)::Number`
  * `Readability.sentences(text::String)::Int`
  * `Readability.sentences_per_paragraph(text::String)::Number`
  * `Readability.smog(text::String)::Number`
  * `Readability.spache(text::String)::Number`
  * `Readability.speaking_time(text::String; wpm::Number=183)::Number`
  * `Readability.syllables(text::String)::Int`
  * `Readability.syllables_per_word(text::String)::Number`
  * `Readability.words(text::String)::Int`
  * `Readability.words_per_sentence(text::String)::Number`
