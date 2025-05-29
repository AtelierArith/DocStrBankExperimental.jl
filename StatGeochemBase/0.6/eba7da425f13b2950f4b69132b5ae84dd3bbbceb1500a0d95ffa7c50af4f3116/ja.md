```julia
delim_string_parse(str, delim, T;
    	merge::Bool=false,
    	undefval=NaN)
```

区切り文字 `delim` を使って区切られた文字列 `str` を型 `T` の値に解析し、結果を型 `T` の配列として返します。

オプションのキーワード引数とデフォルト:

```
merge::Bool=false
```

繰り返される区切り文字をマージしますか？

```
undefval=NaN
```

型 `T` に `parse` できない値の代わりに使用する値。

インプレースバージョンについては `delim_string_parse!` も参照してください。

### 例

```julia
julia> delim_string_parse("1,2,3,4,5", ',', Float64)
5-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
 5.0
```
