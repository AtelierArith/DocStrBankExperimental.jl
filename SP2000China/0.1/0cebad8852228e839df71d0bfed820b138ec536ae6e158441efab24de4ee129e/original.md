`Latin2GenusSpecies(latin_text::String)`

# Description

  * Converts a Latin scientific name to an abbreviated form containing only the genus and species names.

# Parameters

  * `latin_text`: Latin scientific name.

# Results

  * `genus_species`: Abbreviated form containing only the genus and species names.

# Example

```
using SP2000China;
latin_text = "Cotinus coggygria var. pubescens Engl.";
genus_species = Latin2GenusSpecies(latin_text);
println(genus_species)
```
