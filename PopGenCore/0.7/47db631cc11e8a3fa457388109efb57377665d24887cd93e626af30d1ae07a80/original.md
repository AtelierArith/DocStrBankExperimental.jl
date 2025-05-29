```
PopGen.read(infile::String; kwargs...)
```

Wraps the individual file importers to read a file in as a `PopData` object. File type is inferred from the file extension (case insensitive): 

| File Format               | Extensions             | Docstring    |
|:------------------------- |:---------------------- |:------------ |
| delimited                 | `.csv`, `.txt`, `.tsv` | `?delimited` |
| genepop                   | `.gen`, `.genepop`     | `?genepop`   |
| structure                 | `.str`, `.structure`   | `?structure` |
| plink                     | `.bed`, `.ped`         | `?plink`     |
| variant call format (vcf) | `.vcf`, `.vcf.gz`      | `?vcf`       |
| variant call format (bcf) | `.bcf`, `.bcf.gz`      | `?bcf`       |

This function uses the same keyword arguments (and defaults) as the file importing functions it wraps; please see their respective docstrings in the Julia help console. for specific usage details (e.g. `?genepop`).

## Examples

```
PopGen.read("cavernous_assfish.gen", digits = 3)

PopGen.read("juglans_nigra.vcf")
```
