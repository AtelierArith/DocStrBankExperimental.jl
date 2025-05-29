```
function search_chemical(query,cache=cache=ChemicalIdentifiers.SEARCH_CACHE)
```

与えられたクエリに基づいて、CalebBell/Chemicalsからの70000以上の一般的な化合物のデータベースで検索を行い、対象物質の識別子を含むNamed Tupleを返します。

## 例

```
julia>using ChemicalIdentifiers
julia>res = search_chemical("water")
(pubchemid = 962, CAS = (7732, 18, 5), formula = "H2O", MW = 18.01528, smiles = "O", InChI = "H2O/h1H2", InChI_key = "XLYOFNOQVPJJNP-UHFFFAOYSA-N", iupac_nam e = "oxidane", common_name = "water")

#worst case scenario, not found on the present databases
julia> @btime search_chemical("dimethylpyruvic acid22",nothing)
  273.700 μs (264 allocations: 15.05 KiB)
missing

#common compound found in the short database
julia> @btime search_chemical("methane",nothing)
  7.075 μs (57 allocations: 2.97 KiB)
(pubchemid = 297, CAS = (74, 82, 8), formula = "CH4", MW = 16.04246, smiles = "C", InChI = "CH4/h1H4", InChI_key = "VNWKTOKETHGBQD-UHFFFAOYSA-N", iupac_name = "methane", common_name = "methane")
```

クエリは通常文字列であり、可能な場合はその型が自動的に検出されます。サポートされているクエリタイプは次のとおりです。

### PubChemID:

任意の ``<:Integer`（または整数を含む文字列）を使用して

```julia
julia> search_chemical(8003)
(pubchemid = 8003, CAS = (109, 66, 0), formula = "C5H12", MW = 72.14878, smiles =
"CCCCC", InChI = "C5H12/c1-3-5-4-2/h3-5H2,1-2H3", InChI_key = "OFBQJSOFQDEBGM-UHFFFAOYSA-N", iupac_name = "pentane", common_name = "pentane")
```

### CAS登録番号:

整数のタプルまたは `-` で区切られた数字を含む文字列を使用して：

```
julia> search_chemical((67,56,1))
(pubchemid = 887, CAS = (67, 56, 1), formula = "CH4O", MW = 32.04186, smiles = "CO", InChI = "CH4O/c1-2/h2H,1H3", InChI_key = "OKKJLVBELUTLKV-UHFFFAOYSA-N", iupac_name = "methanol", common_name = "methanol")

 search_chemical((67,56,1),nothing) == search_chemical("67-56-1",nothing) #true
```

### SMILES:

`SMILES=` で始まる文字列を使用して：

```
julia> search_chemical("SMILES=N")
(pubchemid = 222, CAS = (7664, 41, 7), formula = "H3N", MW = 17.03052, smiles = "N", InChI = "H3N/h1H3", InChI_key = "QGZKDVFQNNGYKY-UHFFFAOYSA-N", iupac_name = "azane", common_name = "ammonia")
```

### InChI:

`InChI=1/` または `InChI=1S/` で始まる文字列を使用して：

```
julia> search_chemical("InChI=1/C2H4/c1-2/h1-2H2")
(pubchemid = 6325, CAS = (74, 85, 1), formula = "C2H4", MW = 28.05316, smiles = "C=C", InChI = "C2H4/c1-2/h1-2H2", InChI_key = "VGGSQFUCUMXWEO-UHFFFAOYSA-N", iupac_name = "ethene", common_name = "ethene")
```

### InChIキー:

`XXXXXXXXXXXXXX-YYYYYYYYFV-P` のパターンを持つ文字列を使用して：

```
julia> search_chemical("IMROMDMJAWUWLK-UHFFFAOYSA-N")
(pubchemid = 11199, CAS = (9002, 89, 5),
formula = "C2H4O", MW = 44.05256, smiles
= "C=CO", InChI = "C2H4O/c1-2-3/h2-3H,1H2", InChI_key = "IMROMDMJAWUWLK-UHFFFAOYSA-N", iupac_name = "ethenol", common_name
= "ethenol")
```

CASおよびPubChemIDによる検索は、ネイティブ数値型としてエンコードされているため、少し速くなります。他のプロパティは文字列として保存されます。

パッケージは、各クエリを `ChemicalIdentifiers.SEARCH_CACHE` に `Dict{String,Any}` として保存するため、同じ（または類似の）文字列に対する後続のクエリは、データベースでの検索コストを支払う必要がありません。

クエリを保存したくない場合は、`search_chemical(query,nothing)` を使用するか、独自のキャッシュを使用したい場合は、`search_chemical(query,mycache)` を介して独自のキャッシュを渡してください。
