```julia
delim_string_parse!(result, str, delim, [T];
    	offset::Integer=0,
    	merge::Bool=false,
    	undefval=NaN)
```

区切り文字 `delim` を使って区切られた文字列 `str` を型 `T` の値に解析し、入力として提供された事前に割り当てられた `result` 配列に結果を返します。

`T` が明示的に指定されていない場合、`result` 配列の `eltype` がデフォルトで使用されます。

オプションのキーワード引数とデフォルト：

```
offset::Integer=0
```

解析された結果を `result` のインデックス `1+offset` から書き始めます。

```
merge::Bool=false
```

繰り返された区切り文字をマージしますか？

```
undefval=NaN
```

型 `T` に `parse` できない値の代わりに置き換える値。

自動的に結果配列を割り当てる非インプレースバージョンの `delim_string_parse` も参照してください。

### 例

```julia
julia> A = zeros(100);

julia> n = delim_string_parse!(A, "1,2,3,4,5", ',', Float64)
5

julia> A[1:n]
5-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
 5.0
```
