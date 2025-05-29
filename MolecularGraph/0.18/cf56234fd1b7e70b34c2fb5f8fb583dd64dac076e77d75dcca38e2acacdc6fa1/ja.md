```
inchi(molblock::String; options::String = "", verbose::Bool = false) -> Union{String,Nothing}
inchi(mol::MolGraph; options::String = "", verbose::Bool = false) -> Union{String,Nothing}
```

molblock文字列または分子からInChI文字列を生成します。

オプション、例えば「SNon」は「立体情報なし」を指定し、https://github.com/mojaie/libinchi/blob/master/INCHIBASE/src/inchiapi.h で確認できます。
