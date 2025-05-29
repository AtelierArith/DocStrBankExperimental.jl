Create a dictionary with lemma strings as keys to `LexemeUrn`s for lexemes in both the `ls` and `lsx` datasets.  Note that some distinct lemmata may reduce to a single stripped versions, only one of which will appear in this convenience data.

```julia
lexid_dict()
lexid_dict(repodir)

```
