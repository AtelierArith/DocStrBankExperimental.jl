```
    findLabels(label::String, ::Vector{DataType} = allNumerals; pfxList=Vector{String}=[""])
        -> Vector{Tuple{LabelNumeral,Type}}}
```

Given `allNumerals =[AlphaNumeral, RomanNumeral, Int, LookupNumeral, AlphaNumNumeral]`

Finds the `LabelNumeral` that is most suitably matching to the input `String`. `pfxList` provides one or more label prefix values.

The function returns an array of all the matching `LabelNumeral` and the `Type` of numeral that best matches its internal composition. 
