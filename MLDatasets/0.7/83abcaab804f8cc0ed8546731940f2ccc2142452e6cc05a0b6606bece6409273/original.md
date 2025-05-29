```
UD_English(; split=:train, dir=nothing)
UD_English(split=; [dir])
```

A Gold Standard Universal Dependencies Corpus for English, built over the source material of the English Web Treebank LDC2012T13 (https://catalog.ldc.upenn.edu/LDC2012T13).

The corpus comprises 254,825 words and 16,621 sentences,  taken from five genres of web media: weblogs, newsgroups, emails, reviews, and Yahoo! answers.  See the LDC2012T13 documentation for more details on the sources of the sentences.  The trees were automatically converted into Stanford Dependencies and then hand-corrected to Universal Dependencies.  All the basic dependency annotations have been single-annotated, a limited portion of them have been double-annotated,  and subsequent correction has been done to improve consistency. Other aspects of the treebank, such as Universal POS,  features and enhanced dependencies, has mainly been done automatically, with very limited hand-correction.

Authors: Natalia Silveira and Timothy Dozat and             Marie-Catherine de Marneffe and Samuel             Bowman and Miriam Connor and John Bauer and             Christopher D. Manning Website: https://github.com/UniversalDependencies/UD_English-EWT
