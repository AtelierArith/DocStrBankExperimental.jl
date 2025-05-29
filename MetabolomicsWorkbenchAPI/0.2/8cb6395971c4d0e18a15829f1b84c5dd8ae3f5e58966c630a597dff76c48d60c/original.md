```
mw_match(metabolite_name::String) => DataFrame
```

Standardize metabolite name or PubChem/KEGG/HMDB/ChEBI/LIPID MAPS identifier to RefMet, and fetch  refmet name, formula, exact mass, super class, main class, sub class.

## Details:

> The “match” input item performs a search against a customized synonym table in the database. The submitted synonyms are matched in a ‘fuzzy’ manner by dropping the following types of characters from the specified input value: <space>*+-/(){}[]*";@. In addition, some common ion adduct suffixes (e.g. [M+H]+) are removed. The output item is ignored and the following output information is retrieved: refmet*name, formula, exact mass, main class, sub class.


[https://www.metabolomicsworkbench.org/tools/MWRestAPIv1.0.pdf](https://www.metabolomicsworkbench.org/tools/MWRestAPIv1.0.pdf)
