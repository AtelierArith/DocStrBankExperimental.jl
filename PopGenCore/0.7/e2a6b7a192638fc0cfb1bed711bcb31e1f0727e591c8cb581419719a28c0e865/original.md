```
PopGen.write(data::PopData, filename::String, kwargs...)
PopGen.write(data::PopData; filename::String, kwargs...)
```

Writes `PopData` to a specified file type inferred from the extension of `filename =` (case insensitive). Additional keyword arguments `kwargs...` are specific to the intended file type, and are listed in the docstrings of the specific file writer with the format `?filetype`. For example, to find the appropriate keywords for a conversion to Genepop format, call up the `?genepop` docstring.

| File Format | Extensions             | Docstring  |
|:----------- |:---------------------- |:---------- |
| genepop     | `.gen`, `.genepop`     | ?genepop   |
| delimited   | `.csv`, `.txt`, `.tsv` | ?delimited |
| structure   | `.str`, `.structure`   | ?structure |
| plink       | `.ped`                 | ?plink     |
| baypass     | `.baypass`             | ?baypass   |

### Example

```
cats = @nancycats;
fewer_cats = omit(cats, name = samplenames(cats)[1:10]);
PopGen.write(fewer_cats, filename = "filtered_nancycats.gen", digits = 3, format = "h")
```
