`texeq(code::String)`

Take an input string and renders it inside an equation environemnt (numbered) using KaTeX

Equations can be given labels by adding `"\\label{name}"` inside the `code` string and subsequently referenced in other cells using `eqref("name")`

# Note

To avoid the need of doubling backslashes, use the new [`@texeq_str`](@ref) macro if you are on Pluto ≥ v0.17
