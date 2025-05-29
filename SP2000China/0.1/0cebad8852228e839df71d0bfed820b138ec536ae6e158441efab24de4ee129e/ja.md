`Latin2GenusSpecies(latin_text::String)`

# 説明

  * ラテン語の学名を、属名と種名のみを含む省略形に変換します。

# パラメータ

  * `latin_text`: ラテン語の学名。

# 結果

  * `genus_species`: 属名と種名のみを含む省略形。

# 例

```
using SP2000China;
latin_text = "Cotinus coggygria var. pubescens Engl.";
genus_species = Latin2GenusSpecies(latin_text);
println(genus_species)
```
