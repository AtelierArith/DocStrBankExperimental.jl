```
tospec(thing::AbstractDataTransformer)
tospec(thing::DataSet)
tospec(thing::DataCollection)
```

`thing`をTOMLとして書き込むための`Dict`表現を返します。
