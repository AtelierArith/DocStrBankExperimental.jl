The `StripRTF` module exports a single function, [`striprtf(text)`](@ref), that strips all formatting from a string in [Rich Text Format (RTF)](https://en.wikipedia.org/wiki/Rich_Text_Format) to yield "plain text".

This code is a Julia port of the Python [`striprtf` package](https://github.com/joshy/striprtf) by Joshy Cyriac, which in turn is based on [code posted to StackOverflow](https://stackoverflow.com/questions/188545/regular-expression-for-extracting-text-from-an-rtf-string) by Markus Jarderot and Gilson Filho.
