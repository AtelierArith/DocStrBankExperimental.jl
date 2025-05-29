`molParse(txt::AbstractString)::Molecule`

Parses the `txt` argument—something like "CH4", or "(CH3)2(CH2)6"—returning the corresponding `Molecule` object. Bails out if `txt` contains invalid characters, and if all parentheses aren't closed.
