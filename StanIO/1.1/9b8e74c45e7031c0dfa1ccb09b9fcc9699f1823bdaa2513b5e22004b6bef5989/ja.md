```julia
stan_variables(dct, df)

```

`Variable`オブジェクトの辞書とソースDataFrameを与えられた場合、ソース配列から変数を抽出し、正しい次元に再形成します。

## パラメータ

parameters::OrderedDict{String, Variable}

```
`parse_header()`によって返されるような`Variable`オブジェクトの辞書。
```

df::DataFrame

```
抽出するための`read_csvfiles()`または`read_samples(model, :dataframe)`から返されるDataFrame。
```

## 戻り値

```
再形成されたフィールドを持つ、可能性のあるネストされたDataFrame。
```

エクスポート済み。
